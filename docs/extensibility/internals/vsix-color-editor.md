---
title: VSIX Color Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704038"
---
# <a name="vsix-color-editor"></a>Editor de cores do VSIX
A ferramenta Visual Studio Extension Color Editor pode criar e editar cores personalizadas para o Visual Studio. A ferramenta também pode gerar chaves de recursos temáticos para que as cores possam ser usadas em código. Esta ferramenta é útil para fazer cores para uma extensão do Visual Studio que suporta o tema. Esta ferramenta pode abrir arquivos .pkgdef e .xml. Os temas do Visual Studio (arquivos.vstheme) podem ser usados com o Visual Studio Extension Color Editor alterando a extensão de arquivo para .xml. Além disso, os arquivos .vstheme podem ser importados para um arquivo atual .xml.

 ![VSIX Color Editor Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX Color Editor Hero")

 **Arquivos de definição de pacote**

 Os arquivos de definição de pacote (.pkgdef) são os arquivos que definem os temas. As cores em si são armazenadas em arquivos .xml de cor temática, que são compilados em um arquivo .pkgdef. Os arquivos .pkgdef são implantados em locais pesquisáveis do Visual Studio, processados em tempo de execução e mesclados para definir temas.

 **Tokens de cor**

 Um token de cor é composto de quatro elementos:

- **Nome da categoria:** Um agrupamento lógico para um conjunto de cores. Use um nome de categoria existente se já houver cores específicas para o elemento de ia de ia desejado ou grupo de elementos de IU.

- **Nome do token:** Um nome descritivo para os conjuntos de tokens e tokens de cores. Os conjuntos incluem nomes de token sumido (texto) em segundo plano, bem como todos os seus estados, e estes devem ser nomeados para que seja fácil identificar os pares e os estados aos quais eles se aplicam.

- **Valores de cor (ou matizes):** Necessário para cada tema colorido. Crie sempre valores de cor de texto e de fundo em pares. As cores são emparelhadas para o plano de fundo/primeiro plano para que a cor do texto (primeiro plano) seja sempre legível na cor de fundo na qual é desenhada. Essas cores estão ligadas e serão usadas juntas na ui. Se o plano de fundo não for destinado ao uso com texto, não defina uma cor de primeiro plano.

- **Nome da cor do sistema:** Para uso em displays de alto contraste.

## <a name="how-to-use-the-tool"></a>Como usar a ferramenta
 Tanto quanto possível, e se apropriado, as cores existentes do Visual Studio devem ser reutilizadas em vez de fazer novas. No entanto, para casos em que não são definidas cores apropriadas, cores personalizadas devem ser criadas para manter uma extensão com temática compatível.

 **Criando novos tokens de cores**

 Para criar cores personalizadas usando o Visual Studio Extension Color Editor, siga estas etapas:

1. Determine os nomes de categoria e token para os novos tokens de cores.

2. Escolha as tonalidades que o elemento UI usará para cada tema e a cor do sistema para Alto Contraste.

3. Use o editor de cores para criar novos tokens de cores.

4. Use as cores em uma extensão do Visual Studio.

5. Teste as mudanças no Visual Studio.

   **Passo 1: Determine os nomes de categoria e tokens para os novos tokens de cores.**

   O esquema de nomeação preferido para um VSColor é **[Categoria] [tipo de UI] [Estado]**. Não use a palavra "cor" em nomes VSColor, pois é redundante.

   Os nomes das categorias fornecem agrupamentos lógicos e devem ser definidos da forma mais estreita possível. Por exemplo, o nome de uma única janela de ferramenta pode ser um nome de categoria, mas o nome de toda uma unidade de negócios ou equipe de projeto não é. Agrupar entradas em categorias ajuda a evitar confusão entre cores com o mesmo nome.

   Um nome de token deve indicar claramente o tipo de elemento e as situações, ou "estado", para o qual a cor será aplicada. Por exemplo, uma dica de dados ativa **[tipo de IA]** poderia ser nomeada "**DataTip**" e o **[Estado]** poderia ser chamado de "**Ativo**", resultando em um nome de cor de "**DataTipActive**". Como as dicas de dados têm texto, tanto um primeiro plano quanto uma cor de fundo precisam ser definidos. Usando um emparelhamento em segundo plano/primeiro plano, o editor de cores criará automaticamente as cores "**DataTipActive**" para o plano de fundo e "**DataTipActiveText**" para o primeiro plano.

   Se a parte da UI tiver apenas um estado, a parte **[do Estado]** do nome pode ser omitida. Por exemplo, se uma caixa de pesquisa tiver uma borda e não houver nenhuma alteração de estado que afete a cor da borda, então o nome do token de cor da borda pode simplesmente ser chamado de "**SearchBoxBorder**".

   Alguns nomes de estado comuns incluem:

- Ativo

- Inativo

- MouseOver

- Mousedown

- Selecionado

- Focalizado

  Exemplos de alguns nomes de tokens para partes de um controle de item da lista:

- Listitem

- ListItemBorder

- ListItemMouseOver

- ListItemMouseOverBorder

- ListItemSelecionado

- ListItemSelectedBorder

- ListItemDisabled

- ListItemDisabledBorder

  **Passo 2: Escolha as tonalidades que o elemento UI usará para cada tema e a cor do sistema para Alto Contraste.**

  Ao escolher cores personalizadas para iu de ur, selecione um elemento de ia existente semelhante e use suas cores como base. As cores para elementos de iu in-the-box foram submetidas a revisão e testes, de modo que eles vão parecer apropriados e se comportar corretamente em todos os temas.

  **Passo 3: Use o editor de cores para criar novos tokens de cores.**

  Inicie o editor de cores e abra ou crie um novo arquivo de cores temáticas personalizadas .xml. Selecione **Editar > Nova cor** no menu. Isso abre uma caixa de diálogo para especificar a categoria e um ou mais nomes para entradas de cor nessa categoria:

  ![VSIX Color Editor Nova Cor](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX Color Editor Nova Cor")

  Selecione uma categoria existente ou selecione **Nova categoria** para criar uma nova categoria. Outro diálogo será aberto, criando um novo nome de categoria:

  ![VSIX Color Editor Nova Categoria](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX Color Editor Nova Categoria")

  A nova categoria estará disponível no menu suspenso da categoria **Nova Cor.** Depois de escolher uma categoria, digite um nome por linha para cada novo token de cor e selecione "Criar" quando terminar:

  ![Editor de cores VSIX Nova cor preenchido](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "Editor de cores VSIX Nova cor preenchido")

  Os valores de cor são mostrados em pares de fundo/primeiro plano, com "Nenhum" indicando que a cor não foi definida. Nota: se uma cor não tiver um par de cores de texto/de fundo, apenas o plano de fundo precisa ser definido.

  ![Valores de cor do editor de cores VSIX](../../extensibility/internals/media/vsix-color-editor-color-values.png "Valores de cor do editor de cores VSIX")

  Para editar um token de cor, selecione uma entrada de cor para o tema (coluna) desse token. Adicione o valor de cor digitando um valor de cor hexona em formato ARGB de 8 dígitos, digitando um nome de cor do sistema na célula ou usando o menu suspenso para selecionar a cor desejada através de um conjunto de controles deslizantes de cores ou uma lista de cores do sistema.

  ![VSIX Color Editor Editar cor](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX Color Editor Editar cor")

  ![VSIX Fundo do editor de cores](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX Fundo do editor de cores")

  Para componentes que não precisam exibir texto, digite apenas um valor de cor: a cor de fundo. Caso contrário, digite valores para a cor de fundo e texto, separados por uma barra para a frente.

  Ao inserir valores para Alto Contraste, digite nomes de cores válidos do sistema Windows. Não digite valores ARGB codificados. Você pode exibir uma lista de nomes de cores do sistema válidos selecionando "Plano de fundo: sistema" ou "Primeiro plano: sistema" nos menus suspensos de valor de cor. Ao criar elementos que tenham componentes de texto, use o par de cores correto do sistema de fundo/texto ou o texto pode ser ilegível.

  Quando terminar de criar, definir e editar os tokens de cor, salve-os no formato .xml ou .pkgdef desejado. Os tokens de cor com um plano de fundo nem um conjunto em primeiro plano serão salvos como cores vazias no formato .xml, mas descartados no formato .pkgdef. Uma caixa de diálogo irá avisá-lo de uma possível perda de cor se você tentar salvar cores vazias em um arquivo .pkgdef.

  **Passo 4: Use as cores em uma extensão do Visual Studio.**

  Depois de definir os novos tokens de cor, inclua o .pkgdef no arquivo do projeto com "Build Action" definido como "Conteúdo" e "Incluir em VSIX" definido como "True".

  ![VSIX Color Editor pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX Color Editor pkgdef")

  No Visual Studio Extension Color Editor, escolha Arquivo > Exibir código de recursos para visualizar o código usado para acessar as cores personalizadas na UI baseada em WPF.

  ![VSIX Color Editor Resource Code Viewer](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX Color Editor Resource Code Viewer")

  Inclua este código em uma classe estática no projeto. Uma referência ao **Microsoft.VisualStudio.Shell.\< VSVersion>.0.dll** precisa ser adicionado ao projeto para usar o tipo **ThemeResourceKey.**

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 Isso permite o acesso às cores no código XAML e permite que a iu de urao responda às alterações do tema.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **Passo 5: Teste as mudanças no Visual Studio.**

 O editor de cores pode aplicar temporariamente tokens de cor às instâncias em execução do Visual Studio para visualizar alterações ao vivo em cores sem reconstruir o pacote de extensão. Para isso, clique no botão "Aplicar este tema ao executar janelas do Visual Studio" localizado no cabeçalho de cada coluna temática. Este tema temporário desaparecerá quando o Editor de Cores VSIX estiver fechado.

 ![Editor de cores VSIX Aplicar](../../extensibility/internals/media/vsix-color-editor-apply.png "Editor de cores VSIX Aplicar")

 Para tornar as alterações permanentes, reconstrua e reimplante a extensão do Visual Studio depois de adicionar as novas cores ao arquivo .pkgdef e escrever o código que usará essas cores. A reconstrução da extensão do Visual Studio irá mesclar os valores de registro para as novas cores no resto dos temas. Em seguida, reinicie o Visual Studio, visualize a ui e verifique se as novas cores aparecem como esperado.

## <a name="notes"></a>Observações
 Esta ferramenta destina-se a ser usada para criar cores personalizadas para os temas preexistentes do Visual Studio, ou para editar as cores de um tema personalizado do Visual Studio. Para criar temas completos personalizados do Visual Studio, baixe a [extensão do Visual Studio Color Theme Editor](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) da Visual Studio Extensions Gallery.

## <a name="sample-output"></a>Saída de exemplo
 **Saída de cor XML**

 O arquivo .xml gerado pela ferramenta será semelhante a isso:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **Saída de cor PKGDEF**

 O arquivo .pkgdef gerado pela ferramenta será semelhante a isso:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **Ninhado de chaves de recursos C#**

 As chaves de recurso de cor geradas pela ferramenta serão semelhantes a esta:

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **Invólucro do dicionário de recursos WPF**

 As teclas **color ResourceDictionary** geradas pela ferramenta serão semelhantes a esta:

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```
