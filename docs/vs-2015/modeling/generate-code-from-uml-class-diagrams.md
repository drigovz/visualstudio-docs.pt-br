---
title: Gerar código a partir de diagramas de classe UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75120b2f09c2eba3254a1b94e78875d8130c5225
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666126"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Gerar código por meio de diagramas de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para gerar o código do Visual C# .NET de diagramas de classe UML no Visual Studio, use o comando **gerar código** . Por padrão, o comando gera um tipo do C# para cada tipo UML selecionado. É possível modificar e estender esse comportamento modificando ou copiando-se os modelos de texto que geram o código. É possível especificar o comportamento diferente para os tipos contidos em pacotes diferentes do modelo.

 O comando **gerar código** é especialmente adequado à geração de código da seleção de elementos do usuário e à geração de um arquivo para cada classe UML ou outro elemento. Por exemplo, a captura de tela mostra dois arquivos do C# que foram gerados com base em duas classes UML.

 Como alternativa, se você quiser gerar um código no qual os arquivos gerados não tenham uma relação 1:1 com os elementos UML, você pode considerar escrever modelos de texto que são invocados com o comando **transformar todos os modelos** . Para obter mais informações sobre esse método, consulte [gerar arquivos de um modelo UML](../modeling/generate-files-from-a-uml-model.md).

 ![Diagrama de classes UML e arquivos de classe C&#35; gerados.](../modeling/media/oob-gencode1.png "oob_GenCode1")

 Para obter mais informações sobre diagramas de classe UML no Visual Studio, consulte os seguintes tópicos:

- [Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)

- [Diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md)

  Para ver quais versões do Visual Studio oferecem suporte a diagramas de classe UML, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="using-the-generate-code-command"></a>Usando o Comando Gerar Código
 O procedimento a seguir descreve o comportamento padrão do comando **gerar código** :

#### <a name="to-generate-a-separate-file-for-each-element"></a>Para gerar um arquivo separado para cada elemento

1. Crie um modelo UML que contenha classes. Você talvez queira aplicar estereótipos aos elementos de modelo.

    Para obter mais informações, consulte [transformações de geração de código padrão](#default).

2. Em um diagrama de classe ou no **Gerenciador de modelos UML**, selecione os elementos dos quais você deseja gerar o código. É possível selecionar um dos seguintes:

   - Um conjunto específico de elementos.

   - Um pacote ou o modelo, para gerar código com base em seu conteúdo.

   - O diagrama, para selecionar todos os elementos no diagrama.

3. Abra o menu de atalho para um elemento selecionado e, em seguida, escolha **gerar código**.

    Na primeira vez que você usar **gerar código** em um modelo específico, uma caixa de diálogo será exibida. Essa caixa de diálogo permite editar os parâmetros da geração de códigos do modelo.

    Escolha **OK** , a menos que você saiba que deseja alterar esses parâmetros.

    Para retornar a essa caixa de diálogo mais tarde, abra o **Gerenciador de modelos UML**. Abra o menu de atalho de projeto de modelagem e escolha **Configurar geração de código**. Para obter mais informações, consulte [personalização do comando gerar código](#custom).

   Os arquivos que contêm o código do C# são gerados. No caso padrão, um arquivo é gerado para cada tipo, e os arquivos são gerados em um projeto de biblioteca de classes do C#. Porém, é possível personalizar esse comportamento. Para obter mais informações, consulte [personalização do comando gerar código](#custom).

   Alguns testes de validação são aplicados ao modelo para garantir que ele possa ser convertido no C#. Se esse teste falhar, uma mensagem de erro será exibida e a geração de código não será realizada. Se você tiver criado um comando de menu de validação, o código não será gerado para nenhum elemento com falha no comando de validação. Para obter mais informações, consulte [definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="default-code-generation-transforms"></a><a name="default"></a> Transformações de geração de código padrão
 Esta seção resume os resultados produzidos pelo comando **gerar código** , a menos que você personalize o comando. Para obter mais informações, consulte [personalização do comando gerar código](#custom).

- Um tipo do C# é gerado para cada tipo selecionado no modelo UML. Cada tipo é colocado em um arquivo de código separado na pasta **GeneratedCode**

- Se o tipo UML estiver contido em um pacote, o tipo do C# gerado será colocado em um namespace e o arquivo será gerado em uma pasta com o mesmo nome do namespace.

- Uma propriedade do C# é gerada para cada `Attribute` de uma classe UML.

- Um método do C# é gerado para cada `Operation` de um tipo UML.

- Um campo do C# é gerado para cada associação navegável da qual a classe participa.

  Adicionando um estereótipo a cada tipo UML, você pode controlar mais propriedades do tipo do C# gerado.

|**Para criar o tipo do C#**|**Desenhar este tipo UML**|**Aplicar este estereótipo**|
|---------------------------------|----------------------------|-------------------------------|
|Classe|Classe|\<none> ou<br /><br /> Classe do C#|
|Interface|Interface|\<none> ou<br /><br /> Interface do C#|
|Enumeração|Enumeração|\<none> ou<br /><br /> Enum do C#|
|Delegar|Classe|Representante do C#|
|Estrutura|Classe|Struct do C#|

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Para definir um estereótipo em um tipo ou outro elemento

1. Abra o menu de atalho do elemento em um diagrama ou no **Gerenciador de modelos UML**e escolha **Propriedades**.

2. Na janela **Propriedades** , escolha a seta suspensa na propriedade **estereótipos** e marque a caixa de seleção para o estereótipo que você deseja aplicar.

   > [!TIP]
   > Se os estereótipos do C# não forem exibidos, habilite o Perfil do C# para o modelo ou para um pacote que contém os elementos de modelo nos quais você tem interesse. Selecione o pacote ou a raiz do modelo no **Gerenciador de modelos UML**. Em seguida, na janela **Propriedades** , escolha **perfil**e habilite o perfil C#.

3. Expanda a propriedade **estereótipos** para ver as propriedades adicionais que podem ser definidas.

   As propriedades de **Descrição** de tipos, atributos, operações e associações são gravadas em `<summary>` comentários no código gerado. Os elementos de comentário vinculados a tipos são gravados em comentários `<remarks>`.

## <a name="varying-the-generated-code"></a>Variando o código gerado
 O código gerado varia de acordo com as propriedades de cada tipo, atributo ou operação. Por exemplo, se você definir a propriedade **abstract** de uma classe como true, a `abstract` palavra-chave será exibida na classe gerada. Se você definir a **multiplicidade** de um atributo como **0.. \* **, a propriedade gerada terá um `IEnumerable<>` tipo.

 Além disso, cada estereótipo oferece várias propriedades adicionais que é possível definir. Esses valores são convertidos em palavras-chave no código do C#. Por exemplo, se você definir a propriedade `Is Static` em uma classe, a classe do C# será `static`.

 Para definir essas propriedades adicionais, selecione a classe ou outro elemento no diagrama. No janela Propriedades, expanda **estereótipos**e, em seguida, expanda o estereótipo c#, como a **classe c#**.  Para classes, entre essas propriedades adicionais estão:

- Atributos CLR

- Is Partial

- Is Static

- Is Unsafe

- Visibilidade do Pacote

  Cada atributo e operação também tem propriedades de estereótipo que é possível definir. Se você não vir as propriedades em um novo atributo, execute **gerar código**.

## <a name="customizing-the-generate-code-command"></a><a name="custom"></a> Personalizando o comando gerar código
 O comando **gerar código** funciona transformando os elementos do modelo usando um conjunto de modelos de texto. Para obter mais informações sobre modelos de texto, consulte [geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md).

 Os modelos são especificados em um conjunto de *associações de modelo de texto*. Uma associação de modelo de texto especifica qual modelo deve ser aplicado, onde a saída gerada deve ser colocada e outros parâmetros do comando de **geração de código** .

 Quando você executa pela primeira vez o comando **gerar código** em um modelo específico, ele anexa um conjunto padrão de associações de modelo à raiz do modelo. Essas associações se aplicam a todos os elementos no modelo.

 Porém, você pode substituir e adicionar a essas associações padrão anexando as próprias associações a pacotes, classes ou outros elementos. Uma associação se aplica a todos os elementos contidos dentro do elemento ao qual é anexada. Por exemplo, se quiser que todos os tipos em um pacote específico sejam transformados por um conjunto diferente de modelos ou colocados em uma pasta diferente, você poderá anexar associações de modelo ao pacote.

 Para inspecionar as associações de modelo anexadas a um elemento de modelo, escolha as reticências **[...]** na propriedade **associações de modelo de texto** no janela Propriedades.

 O comando **gerar código** aplica modelos a cada elemento de modelo que você selecionou. Para cada elemento, o conjunto de modelos aplicado é o conjunto combinado de modelos anexados a seus contêineres, até e incluindo a raiz do modelo.

 Se duas associações de modelo nesse conjunto tiverem o mesmo nome, a associação no contêiner menor substituirá a associação no contêiner maior. Por exemplo, a raiz do modelo tem uma associação com o **modelo de classe**de nome. Para ter seu próprio modelo aplicado ao conteúdo de um pacote específico, defina sua própria associação de modelo que tenha o **modelo de classe**de nome.

 Mais de um modelo pode ser aplicado a um elemento de modelo. É possível gerar mais de um arquivo de cada elemento de modelo.

> [!NOTE]
> As associações anexadas à raiz do modelo funcionam como padrões para todos os elementos no modelo. Para ver essas associações padrão, abra o **Gerenciador de modelos UML**. Abra o menu de atalho do projeto de modelagem e escolha **Configurar geração de código**. Como alternativa, você pode selecionar a raiz do modelo no Gerenciador de modelos UML. Na janela Propriedades, escolha **[...]** na propriedade **associações de modelo de texto** . As associações não serão exibidas até que você tenha usado o comando **gerar código** pelo menos uma vez. As associações de modelo não podem ser anexadas a um diagrama.

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Para anexar associações do modelo de texto a um pacote ou a outro elemento de modelo

1. No **Gerenciador de modelos UML**, abra o menu de atalho de um elemento de modelo e escolha **Propriedades**. Você normalmente anexaria associações do modelo de texto a um pacote ou à raiz do modelo.

2. Na janela **Propriedades** , escolha o botão de reticências (**[...]**) na propriedade **associações de modelo de texto** .

    A caixa de diálogo **associações de modelo de texto** é exibida.

3. Escolha **Adicionar** para criar uma nova associação de modelo de texto.

    \- ou –

    Escolha uma associação existente para editá-la.

    Cada associação de modelo define como um modelo especificado deve ser aplicado ao elemento de modelo selecionado, além de outros elementos de modelo contidos.

4. Na caixa de diálogo, defina as propriedades da associação do modelo de texto.

   |    **Propriedade**    |                                                                                                                                                                                                                                                                                                                    **Descrição**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Nome        |                                                                                                                                                                                                                                                  Um nome da associação. Para substituir uma associação herdada de um pacote ou de um modelo de conteúdo, use o mesmo nome da associação que você deseja substituir.                                                                                                                                                                                                                                                  |
   |     Overwrite      |                                                                                                                                                                                                                                                                                                      Se for verdadeiro, todo o código existente será substituído.                                                                                                                                                                                                                                                                                                       |
   |    Nome de destino     | O nome do arquivo gerado.<br /><br /> Você pode inserir expressões nessa cadeia de caracteres, como `{Name}` ou `{Owner.Name}` . Por exemplo, você poderia escrever: `{Owner.Name}_{Name}` . A expressão é avaliada no elemento de modelo. Ela pode usar propriedades de elementos, mas não métodos. Para localizar quais propriedades podem ser usadas, examine as propriedades de tipos em **Microsoft. VisualStudio. Uml. \* **. \*\*Importante: \* \* `{Name}` ou `{Owner.Name}` pode ser usado somente na propriedade **nome de destino** .   Para alterar o nome da classe gerado, você precisa modificar o modelo. Para obter mais informações, consulte [escrevendo um modelo de texto](#writing). |
   |    Caminho do Projeto    |                                                                      Especifica o caminho para o projeto do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que conterá os arquivos de saída da transformação. Use valores digitados para criar um novo projeto. Escolha o botão de reticências (**[...]**) para selecionar um projeto existente.<br /><br /> Se não existir, um novo projeto será criado. Ele será um projeto de biblioteca de classes do C#.<br /><br /> Para isso, você deve digitar o projeto diretamente. É possível incluir macros da variável de ambiente como %ProgramFiles% ou %LocalAppData%.                                                                       |
   |  Diretório de destino  |                                                                                          A pasta na qual o arquivo de destino é gerado. O caminho se refere à pasta do projeto.<br /><br /> É possível usar a expressão `{PackageStructure}` para inserir um caminho correspondente aos nomes dos pacotes de contenção. O valor padrão é `\GeneratedCode\{PackageStructure}`. Também é possível incluir variáveis de ambiente como %TEMP% ou %HomePath%. **Importante:** `{PackageStructure}` pode ser usado somente na propriedade **diretório de destino** .                                                                                            |
   | Caminho do Arquivo de Modelo |                                                                                                                                                           O modelo que realizará a transformação.<br /><br /> É possível usar os modelos fornecidos ou criar os próprios. É possível encontrar os modelos fornecidos no seguinte local:<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. É possível anexar quantas associações a um elemento você quiser.

## <a name="writing-a-text-template"></a><a name="writing"></a> Escrevendo um modelo de texto
 É possível gravar os próprios modelos de texto. Os modelos de texto podem gerar códigos de programa ou qualquer outro tipo de arquivo de texto.

 Recomendamos que você comece modificando cópias dos modelos padrão. É possível copiar os modelos dos seguintes locais:

 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\

 Para compreender os modelos de texto, consulte os tópicos a seguir.

- Um modelo de texto é um protótipo do arquivo resultante e contém o texto resultante e o código do programa que lê o modelo. Para obter mais informações, consulte [geração de código e modelos de texto T4](../modeling/code-generation-and-t4-text-templates.md).

- Para navegar no modelo UML no código do programa, você precisa usar a API UML. Para obter mais informações, consulte [navegar no modelo UML](../modeling/navigate-the-uml-model.md) e [referência de API para EXTENSIBILIDADE de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md).

  Para usar os modelos com o comando **gerar código** , você deve incluir a diretiva de modelagem. Por exemplo:

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`

  O atributo `ElementType` define o tipo de elemento UML ao qual esse modelo se aplica.

  No modelo, `this` pertence a uma classe temporária com as seguintes propriedades:

- `Element` = o [IELEMENTO](/previous-versions/dd516035(v=vs.140)) UML ao qual o modelo está sendo aplicado.

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>

- `Host`: [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

- `ModelBus`: [ModelBus](/previous-versions/ee904639(v=vs.140)). Para obter mais informações, consulte [integrar modelos UML com outros modelos e ferramentas](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- `ProfileName` = "Perfil C #"

- `ServiceProvider`: <xref:System.IServiceProvider>

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Este é o Repositório do SDK de Visualização e Modelagem no qual o ModelStore UML é implementado. Para obter o [IMODELSTORE](/previous-versions/ee789385(v=vs.140))UML, use `this.Element.GetModelStore()` .

  Você talvez ache os pontos a seguir úteis ao gravar um modelo de texto. Essas informações são descritas em detalhes nos [modelos de texto de geração de código e T4](../modeling/code-generation-and-t4-text-templates.md).

- É possível definir a extensão de nome de arquivo do resultado na diretiva `Output`. Uma diretiva `Output` é obrigatória em todo modelo de texto.

- Alguns assemblies são referenciados automaticamente pelo modelo. Entre esses assemblies, por exemplo, System.dll e Microsoft.VisualStudio.Uml.Interfaces.dll.

   Para usar outros assemblies no código de programa da geração, você deve usar uma diretiva `Assembly`. Por exemplo:

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`

- Alguns namespaces como `System` são importados automaticamente no código de programa. Para outros namespaces, é possível usar a diretiva `Import` da mesma maneira que você usaria uma instrução `using`. Por exemplo:

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`

- Use a diretiva `Include` para fazer referência ao texto de outro arquivo.

- As partes do modelo entre colchetes `<# ... #>` são executadas pelo comando **gerar código** . As partes do modelo fora desses colchetes são copiadas para o arquivo de resultado. É importante distinguir o código de geração do texto gerado. O texto gerado pode estar em qualquer linguagem.

- `<#= Expressions #>` são avaliados e convertidos em cadeias de caracteres.

## <a name="see-also"></a>Consulte Também
 [Diagramas de classe UML: referenciar](../modeling/uml-class-diagrams-reference.md) [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md) [geram arquivos de um modelo UML](../modeling/generate-files-from-a-uml-model.md)
