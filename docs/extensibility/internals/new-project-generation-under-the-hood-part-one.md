---
title: 'Nova geração de projetos: Sob o capô, Parte Um | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707061"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Geração de novo projeto: nos bastidores, Parte um
Já pensou em como criar seu próprio tipo de projeto? O que realmente acontece quando você cria um novo projeto? Vamos dar uma olhada debaixo do capô e ver o que realmente está acontecendo.

 Existem várias tarefas que o Visual Studio coordena para você:

- Ele exibe uma árvore de todos os tipos de projetos disponíveis.

- Ele exibe uma lista de modelos de aplicativos para cada tipo de projeto e permite que você escolha um.

- Ele coleta informações do projeto para o aplicativo, como nome do projeto e caminho.

- Ele passa essa informação para a fábrica do projeto.

- Ele gera itens de projeto e pastas na solução atual.

## <a name="the-new-project-dialog-box"></a>A caixa de diálogo do novo projeto
 Tudo começa quando você seleciona um tipo de projeto para um novo projeto. Vamos começar clicando em **Novo Projeto** no menu **Arquivo.** A caixa de diálogo **Novo Projeto** aparece, algo assim:

 ![Caixa de diálogo Novo Projeto](../../extensibility/internals/media/newproject.gif "NewProject")

 Vamos analisar com mais detalhes. A **árvore tipos de projeto** lista os vários tipos de projeto que você pode criar. Quando você seleciona um tipo de projeto como **Visual C# Windows,** você verá uma lista de modelos de aplicativos para começar. **Os modelos instalados do Visual Studio** são instalados pelo Visual Studio e estão disponíveis para qualquer usuário do seu computador. Novos modelos que você cria ou coleta podem ser adicionados aos **Meus Modelos** e estão disponíveis apenas para você.

 Quando você seleciona um modelo como **O Aplicativo do Windows**, uma descrição do tipo de aplicativo aparece na caixa de diálogo; neste caso, **um projeto para criar um aplicativo com uma interface de usuário do Windows**.

 Na parte inferior da caixa de diálogo **Projeto Novo,** você verá vários controles que coletam mais informações. Os controles que você vê dependem do tipo de projeto, mas geralmente incluem uma caixa de texto **nome do** projeto, uma caixa de texto **de Localização** e um botão de **Navegação** relacionado, e uma caixa de texto Nome **da solução** e diretório de Criação relacionado para caixa de seleção **de solução.**

## <a name="populating-the-new-project-dialog-box"></a>Povoando a caixa de diálogo do novo projeto
 De onde a caixa de diálogo **Do Novo Projeto** recebe suas informações? Há dois mecanismos em ação aqui, um deles preterido. A caixa de diálogo **Novo Projeto** combina e exibe as informações obtidas de ambos os mecanismos.

 O método mais antigo (depreciado) usa entradas de registro do sistema e arquivos .vsdir. Este mecanismo funciona quando o Visual Studio abriu. O método mais novo usa arquivos .vstemplate. Este mecanismo é executado quando o Visual Studio é inicializado, por exemplo, executando

```
devenv /setup
```

 ou

```
devenv /installvstemplates
```

### <a name="project-types"></a>Tipos de projeto
 A posição e os nomes dos nós raiz do **Projeto,** como **Visual C#** e **Outras Línguas,** são determinados por entradas de registro do sistema. A organização dos nós infantis, como Banco de **Dados** e **Dispositivo Inteligente,** espelha a hierarquia das pastas que contêm os arquivos .vstemplate correspondentes. Vamos olhar para os nódulos raiz primeiro.

#### <a name="project-type-root-nodes"></a>Nóraiz tipo de projeto
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é inicializado, ele atravessa as subchaves da chave de registro do sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\Templates\Templates para criar e nomear os nós raiz da árvore **tipos de projeto.** Essas informações são armazenadas em cache para uso posterior. Veja a tecla\\TemplateDirs {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}\\/1. Cada entrada é um VSPackage GUID. O nome da subchave (/1) é ignorado, mas sua presença indica que este é um nó raiz **tipo Projeto.** Um nó raiz pode, por sua vez, ter várias subteclas que controlam sua aparência na árvore **tipos de projeto.** Vamos olhar para alguns deles.

##### <a name="default"></a>(Padrão)
 Este é o ID de recurso da seqüência localizada que nomeia o nó raiz. O recurso string está localizado no satélite DLL selecionado pelo VSPackage GUID.

 No exemplo, o VSPackage GUID é

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 e o ID de recurso (valor padrão) do nó raiz (/1) está #2345

 Se você procurar o GUID na tecla Pacotes próximo e examinar a subchave SatelliteDll, você poderá encontrar o caminho do conjunto que contém o recurso string:

 \<Caminho de instalação do Visual Studio>\VC#\VCSPacotes\1033\csprojui.dll

 Para verificar isso, abra o File Explorer e arraste csprojui.dll para o diretório do Visual Studio.. A tabela de strings mostra que o #2345 de recursos tem a legenda **Visual C#**.

##### <a name="sortpriority"></a>ClassificarPrioridade
 Isso determina a posição do nó raiz na árvore **tipos de projeto.**

 SortPriority REG_DWORD 0x0000014 (20)

 Quanto menor o número de prioridade, maior a posição na árvore.

##### <a name="developeractivity"></a>Atividade do desenvolvedor
 Se esta subchave estiver presente, a posição do nó raiz será controlada pela caixa de diálogo Configurações do desenvolvedor. Por exemplo,

 Atividade do desenvolvedor REG_SZ VC #

 indica que visual C# será um nó raiz [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] se o Visual Studio estiver pronto para o desenvolvimento. Caso contrário, será um nó infantil de **outras línguas.**

##### <a name="folder"></a>Pasta
 Se esta subchave estiver presente, então o nó raiz se tornará um nó filho da pasta especificada. Uma lista de pastas possíveis aparece sob a chave

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoPasts

 Por exemplo, a entrada Projetos de banco de dados tem uma tecla Pasta que corresponde à entrada de outros tipos de projeto em PseudoPasts. Assim, na árvore **tipos de projeto,** **projetos de banco de dados** serão um nó infantil de outros tipos de **projeto.**

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Tipos de projeto de nós infantis e arquivos .vstdir
 A posição dos nós filho na árvore **Tipos de Projeto** segue a hierarquia das pastas nas pastas ProjectTemplates. Para modelos de máquinas **(modelos instalados pelo Visual Studio),** a localização típica é \Arquivos do programa\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ e para modelos de\\usuário **(Meus modelos),** a localização típica é \Meus Documentos\Visual Studio 14.0\Templates\ProjectTemplates . As hierarquias de pastas desses dois locais são mescladas para criar a árvore **tipos de projeto.**

 Para o Visual Studio com configurações de desenvolvedor C#, a árvore **tipos de projeto** se parece com algo assim:

 ![Tipos de projeto](../../extensibility/internals/media/projecttypes.png "Tipos de projetos")

 A pasta ProjectTemplates correspondente é assim:

 ![Modelos de projeto](../../extensibility/internals/media/projecttemplates.png "Modelos de projeto")

 Quando a caixa de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diálogo Novo **Projeto** é aberta, atravessa a pasta ProjectTemplates e recria sua estrutura na árvore tipos de **projeto** com algumas alterações:

- O nó raiz na árvore **Tipos de Projeto** é determinado pelo modelo do aplicativo.

- O nome do nó pode ser localizado e pode conter caracteres especiais.

- A ordem de classificação pode ser alterada.

##### <a name="finding-the-root-node-for-a-project-type"></a>Encontrar o nó raiz para um tipo de projeto
 Quando o Visual Studio atravessa as pastas ProjectTemplates, ele abre todos os arquivos .zip e extrai quaisquer arquivos .vstemplate. Um arquivo .vstemplate usa XML para descrever um modelo de aplicativo. Para obter mais informações, consulte [New Project Generation: Under the Hood, Parte Dois](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 A \<> ProjectType determina o tipo de projeto para o aplicativo. Por exemplo, o \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip existe um arquivo EmptyProject.vstemplate que tem essa tag:

```
<ProjectType>CSharp</ProjectType>
```

 A \<tag ProjectType>, e não a subpasta na pasta ProjectTemplates, determina o nó raiz de um aplicativo na árvore **tipos de projeto.** No exemplo, os aplicativos do Windows CE apareceriam sob o nó raiz **Visual C#** e, mesmo se você fosse mover a pasta do WindowsCE para a pasta VisualBasic, os aplicativos do Windows CE ainda apareceriam sob o nó raiz **Visual C#.**

##### <a name="localizing-the-node-name"></a>Localização do nome do nó
 Quando o Visual Studio atravessa as pastas ProjectTemplates, ele examina todos os arquivos .vstdir que encontrar. Um arquivo .vstdir é um arquivo XML que controla a aparência do tipo de projeto na caixa de diálogo **Projeto** Novo. No arquivo .vstdir, \<use a marca LocalizedName> para nomear o nó **tipo Projeto.**

 Por exemplo, o arquivo \CSharp\Database\TemplateIndex.vstdir contém essa tag:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Isso determina o DLL do satélite e o ID de recurso da seqüência localizada que nomeia o nó raiz, neste caso, **Database**. O nome localizado pode conter caracteres especiais que não estão disponíveis para nomes de pastas, como **.NET**.

 Se \<não houver nenhuma tag localizedName>, o tipo de projeto será nomeado pela própria pasta, **SmartPhone2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Encontrando a ordem de classificação para um tipo de projeto
 Para determinar a ordem de tipo do tipo de \<projeto, os arquivos .vstdir usam a tag SortOrder>.

 Por exemplo, o arquivo \CSharp\Windows\Windows.vstdir contém esta tag:

```
<SortOrder>5</SortOrder>
```

 O arquivo \CSharp\Database\TemplateIndex.vstdir tem uma tag com um valor maior:

```
<SortOrder>5000</SortOrder>
```

 Quanto menor \<o número na tag SortOrder>, maior a posição na árvore, de modo que o nó do **Windows** aparece maior do que o nó Banco de **dados** na árvore tipos de **projeto.**

 Se \<nenhuma tag sortOrder> for especificada para um tipo de projeto, \<ela será exibida em ordem alfabética seguindo quaisquer tipos de projeto que contenham especificações de> do SortOrder.

 Observe que não há arquivos .vstdir nas pastas Meus**Documentos (Meus Modelos).** Os nomes do tipo de projeto do aplicativo de usuário não são localizados e aparecem em ordem alfabética.

#### <a name="a-quick-review"></a>Uma revisão rápida
 Vamos modificar a caixa de diálogo **Novo Projeto** e criar um novo modelo de projeto de usuário.

1. Adicione uma subpasta MyProjectNode à pasta \Program Files\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp.

2. Crie um arquivo MyProject.vstdir na pasta MyProjectNode usando qualquer editor de texto.

3. Adicione essas linhas ao arquivo .vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Salve e feche o arquivo .vstdir.

5. Crie um arquivo MyProject.vstemplate na pasta MyProjectNode usando qualquer editor de texto.

6. Adicione essas linhas ao arquivo .vstemplate:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Salve o arquivo.vstemplate e feche o editor.

8. Envie o arquivo .vstemplate para uma nova pasta compactada MyProjectNode\MyProject.zip.

9. Na janela de comando do Visual Studio, digite:

    ```
    devenv /installvstemplates
    ```

   Abra o Visual Studio.

10. Abra a caixa de diálogo **do Novo Projeto** e expanda o nó do projeto Visual **C#.**

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** aparece como um nó infantil do Visual C# logo abaixo do nó do Windows.

## <a name="see-also"></a>Confira também
- [Geração de novo projeto: nos bastidores, Parte dois](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
