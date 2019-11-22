---
title: Definir um item de caixa de ferramentas de modelagem personalizado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac299f18e544ef4f3215707abbdc3d9e8d266de6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299299"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Definir um item de caixa de ferramentas de modelagem personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para facilitar a criação de um elemento ou grupo de elementos de acordo com um padrão que você usa com frequência, você pode adicionar novas ferramentas à caixa de ferramentas de diagramas de modelagem no Visual Studio. Você pode distribuir esses itens da caixa de ferramentas para outros usuários do Visual Studio.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Uma ferramenta personalizada cria um ou mais novos elementos em um diagrama. Por exemplo, você pode fazer uma ferramenta personalizada para criar elementos como estes:

- Um pacote vinculado ao perfil do .NET e uma classe com o estereótipo .NET.

- Um par de classes vinculadas por uma associação para representar o padrão observador.

> [!NOTE]
> Você pode usar esse método para criar ferramentas de elemento. Ou seja, você pode criar ferramentas que você arrasta da caixa de ferramentas para um diagrama. Você não pode criar ferramentas de conector.

## <a name="DefineTool"></a>Definindo uma ferramenta de modelagem personalizada

#### <a name="to-define-a-custom-modeling-tool"></a>Para definir uma ferramenta de modelagem personalizada

1. Crie um diagrama UML que contenha um elemento ou grupo de elementos.

    - Esses elementos podem ter relações entre eles e podem ter elementos subsidiários, como portas, atributos, operações ou Pins.

2. Salve o diagrama usando o nome que você deseja dar à nova ferramenta. No menu **arquivo** , use **salvar... Como**.

3. Usando o Windows Explorer, copie os dois arquivos de diagrama para a seguinte pasta ou qualquer subpasta:

     *YourDocuments* **\Visual Studio\Architecture Tools\Custom caixa de ferramentas**

    - Crie essa pasta se ela ainda não existir. Talvez seja necessário criar ferramentas de **arquitetura** e **itens de caixa de ferramentas personalizados**.

    - Copie os dois arquivos de diagrama, um com um nome que termine "... **diagrama**"e o outro com um nome que termina com"... **Diagram. layout**"

    - Você pode fazer quantas ferramentas personalizadas desejar. Use um diagrama para cada ferramenta.

4. Adicional Crie um arquivo **. tbxinfo** conforme descrito em [como definir as propriedades de ferramentas personalizadas](#tbxinfo)e adicione-o ao mesmo diretório. Isso permite que você defina um ícone da caixa de ferramentas, uma dica de ferramenta e assim por diante.

    - Um único arquivo **. tbxinfo** pode ser usado para definir várias ferramentas. Ele pode se referir a arquivos de diagrama que estão em subpastas.

5. Reinicie o Visual Studio. A ferramenta adicional aparecerá na caixa de ferramentas para o tipo apropriado de diagrama.

### <a name="what-the-custom-tool-will-replicate"></a>O que a ferramenta personalizada replicará
 Uma ferramenta personalizada replicará a maioria dos recursos do diagrama de origem:

- Nomes. Quando um item é criado na caixa de ferramentas, um número é adicionado ao final do nome, se necessário, para evitar nomes duplicados no mesmo namespace.

- Cores, tamanhos e formas

- Estereótipos e perfis de pacote

- Valores de propriedade como é abstrato

- Itens de trabalho vinculados

- Multiplicidades e outras propriedades de relações

- As posições relativas das formas.

  Os recursos a seguir não serão preservados em uma ferramenta personalizada:

- Formas simples. Essas são formas que não estão relacionadas a elementos de modelo, que você pode desenhar em alguns tipos de diagramas.

- Roteamento de conector. Se você rotear conectores manualmente, o roteamento não será preservado quando sua ferramenta for usada. As posições de algumas formas aninhadas, como portas, não são preservadas em relação aos seus proprietários.

## <a name="tbxinfo"></a>Como definir as propriedades de ferramentas personalizadas
 Um arquivo de informações da caixa de ferramentas ( **. tbxinfo**) permite que você especifique um nome de caixa de ferramentas, ícone, dica de ferramenta, guia e palavra-chave de ajuda para uma ou mais ferramentas personalizadas. Dê a ele qualquer nome, como **MyTools. tbxinfo**.

 A forma geral do arquivo é a seguinte:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 O valor de cada item pode ser:

- Conforme mostrado no exemplo, `<bmp fileName="…"/>` para o ícone caixa de ferramentas e `<value>string</value>` para os outros itens.

  \- ou -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   Nesse caso, você fornece um assembly compilado no qual os valores da cadeia de caracteres foram compilados como recursos.

  Adicione um nó `<customToolboxItem>` para cada item da caixa de ferramentas que você deseja definir.

  Os nós no arquivo **. tbxinfo** são os seguintes. Há um valor padrão para cada nó.

|Nome do nó|Autor|
|---------------|-------------|
|displayName|O nome do item da caixa de ferramentas.|
|tabName|A guia caixa de ferramentas na qual o item deve aparecer. Você pode especificar o nome da guia regular para este tipo de diagrama ou um nome separado.|
|imagem|O local do arquivo de bitmap ( **. bmp**), que deve ter altura e largura de 16 e uma intensidade de cor de 24 bits.|
|f1Keyword|A palavra-chave que localiza um tópico da ajuda.|
|dessa|Uma dica de ferramentas para esta ferramenta.|

 Você pode editar o arquivo de bitmap no Visual Studio e definir sua altura e largura como 16 no janela Propriedades.

> [!NOTE]
> Se você começar a usar um arquivo. tbxinfo depois de experimentar usando arquivos de diagrama por conta própria, talvez descubra que a caixa de ferramentas contém as versões antiga e nova de um item da caixa de ferramentas. Isso também pode ocorrer se o nome do arquivo de diagrama tiver sido digitado no arquivo. tbxinfo. Se isso ocorrer, no menu de atalho da caixa de ferramentas, escolha **Redefinir caixa de ferramentas**. Os itens da caixa de ferramentas personalizada desaparecerão. Reinicie o Visual Studio e os itens personalizados corretos serão exibidos.

## <a name="Extension"></a>Como distribuir itens da caixa de ferramentas em uma extensão do Visual Studio
 Você pode distribuir itens da caixa de ferramentas para outros usuários [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] empacotando-os em uma extensão do Visual Studio (VSIX). Você pode empacotar comandos, perfis e outras extensões no mesmo arquivo VSIX. Para obter mais informações, consulte [implantando extensões do Visual Studio](https://go.microsoft.com/fwlink/?LinkId=160780).

 A maneira usual de criar uma extensão do Visual Studio é usar o modelo de projeto VSIX. Para fazer isso, você deve ter o [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]instalado.

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Para adicionar um item da caixa de ferramentas a uma extensão do Visual Studio

1. [Crie e teste uma ou mais ferramentas personalizadas](#DefineTool).

2. [Crie um arquivo. tbxinfo](#tbxinfo) que faça referência às ferramentas.

3. Abra um projeto de extensão existente do Visual Studio.

     \- ou -

     Defina um novo projeto de extensão do Visual Studio.

    1. No menu **Arquivo**, escolha **Novo**, **Projeto**.

    2. Na caixa de diálogo **novo projeto** , em **modelos instalados**, escolha **Visual C#** , **extensibilidade**e **projeto VSIX**.

4. Adicione suas definições de caixa de ferramentas ao projeto. Inclua o arquivo **. tbxinfo** , os arquivos de diagrama, os arquivos de bitmap e os arquivos de recurso e verifique se eles estão incluídos no VSIX.

    - No Gerenciador de Soluções, no menu de atalho do projeto VSIX, escolha **Adicionar**, **Item existente**. Na caixa de diálogo, defina **objetos do tipo: todos os arquivos**. Localize os arquivos, selecione todos eles e, em seguida, escolha **Adicionar**.

        > [!NOTE]
        > Neste projeto, você não pode abrir os arquivos de diagrama no editor de modelo.

5. Defina as propriedades a seguir de todos os arquivos que você acabou de adicionar. Você pode definir suas propriedades ao mesmo tempo selecionando-as em Gerenciador de Soluções. Tenha cuidado para não alterar as propriedades dos outros arquivos no projeto.

     **Copiar para o diretório de saída** = **copiar sempre**

     **Compilar** **conteúdo** de = de ação

     **Incluir no VSIX** = **verdadeiro**

6. Open **Source. Extension. vsixmanifest**. Ele é aberto no editor de manifesto de extensão.

7. Em **metadados**, adicione uma descrição para as ferramentas personalizadas.

     Em **ativos**, escolha **novo** e, em seguida, defina os campos na caixa de diálogo da seguinte maneira:

    - **Tipo** = **tipo de extensão personalizada**

    - Tipo = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Essa não é uma das opções na lista suspensa. Você precisa inseri-lo usando o teclado.

    - **Arquivo de = de origem no sistema de arquivos**.

    - **Caminho** = seu arquivo **. tbxinfo** , por exemplo, **MyTools. tbxinfo**

8. Compile o projeto.

9. **Para verificar se a extensão funciona**, pressione F5. A instância experimental do Visual Studio é iniciada.

     Na instância experimental, crie ou abra um diagrama UML do tipo relevante. Verifique se a nova ferramenta aparece na caixa de ferramentas e se ela cria elementos corretamente.

10. **Para obter um arquivo VSIX para implantação:** No Windows Explorer, abra a pasta **.\bin\Debug** ou **.\bin\Release** para localizar o arquivo **. vsix** . Este é um arquivo de extensão [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Ele pode ser instalado em seu computador e também enviado para outros usuários do Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Para instalar ferramentas personalizadas de uma extensão do Visual Studio

1. Abra o arquivo `.vsix` no Windows Explorer ou no Visual Studio.

2. Escolha **instalar** na caixa de diálogo exibida.

3. Para desinstalar ou desabilitar temporariamente a extensão, abra **extensões e atualizações** no menu **ferramentas** .

## <a name="localization"></a>Localização
 Você pode fazer uma extensão que, quando instalada em outro computador, exibirá nomes de ferramentas e dicas de ferramenta no idioma do computador de destino.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Para fornecer versões da ferramenta em mais de um idioma

1. Crie um projeto de extensão do Visual Studio que contenha uma ou mais ferramentas personalizadas.

    No arquivo **. tbxinfo** , use o método do arquivo de recurso para definir o `displayName`, a caixa de ferramentas `tabName`e a dica de ferramenta da ferramentas. Crie um arquivo de recurso no qual essas cadeias de caracteres são definidas, compile-o em um assembly e consulte-o no arquivo tbxinfo.

2. Crie assemblies adicionais que contenham arquivos de recursos com cadeias de caracteres em outras linguagens.

3. Coloque cada assembly adicional em uma pasta cujo nome é o código de cultura do idioma. Por exemplo, coloque uma versão em francês do assembly dentro de uma pasta chamada **fr**.

4. Você deve usar um código de cultura neutro, normalmente duas letras, não uma cultura específica, como `fr-CA`. Para obter mais informações sobre códigos de cultura, consulte o [método CultureInfo. Getculturals](https://go.microsoft.com/fwlink/?LinkId=160782), que fornece uma lista completa de códigos de cultura.

5. Crie a extensão do Visual Studio e distribua-a.

6. Quando a extensão é instalada em outro computador, a versão do arquivo de recurso para a cultura local do usuário será carregada automaticamente. Se você não tiver fornecido uma versão para a cultura do usuário, os recursos padrão serão usados.

   Você não pode usar esse método para instalar versões diferentes do diagrama de protótipo. Os nomes de elementos e conectores serão os mesmos em todas as instalações.

## <a name="other-toolbox-operations"></a>Outras operações da caixa de ferramentas
 Normalmente, no [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], você pode personalizar a caixa de ferramentas renomeando as ferramentas, movendo-as para diferentes guias da caixa de ferramentas e excluindo-as. Mas essas alterações não persistem para ferramentas de modelagem personalizadas criadas com os procedimentos descritos neste tópico. Quando você reiniciar [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], as ferramentas personalizadas reaparecerão com seus nomes definidos e locais da caixa de ferramentas.

 Além disso, suas ferramentas personalizadas desaparecerão se você executar o comando **Redefinir caixa de ferramentas** . No entanto, eles serão reexibidos quando você reiniciar [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

## <a name="see-also"></a>Consulte também
 [Estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md) [definir um perfil para estender UML](../modeling/define-a-profile-to-extend-uml.md) [definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md)
