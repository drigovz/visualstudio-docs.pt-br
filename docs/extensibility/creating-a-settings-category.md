---
title: Criando uma categoria de configurações | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739613"
---
# <a name="create-a-settings-category"></a>Criar uma categoria de configurações

Neste passo a passo, você cria uma categoria de configurações do Visual Studio e a usa para salvar valores e restaurar valores de um arquivo de configurações. Uma categoria de configurações é um grupo de propriedades relacionadas que aparecem como um "ponto de configurações personalizado"; ou seja, como uma caixa de seleção no assistente **de Configurações de Importação e Exportações.** (Você pode encontrá-lo no menu **Ferramentas.)** As configurações são salvas ou restauradas como uma categoria, e as configurações individuais não são exibidas no assistente. Para obter mais informações, confira [Configurações do ambiente](../ide/environment-settings.md).

Você cria uma categoria de configurações, derivando-a da <xref:Microsoft.VisualStudio.Shell.DialogPage> classe.

Para iniciar este passo a passo, você deve primeiro concluir a primeira seção da [página Criar uma opção](../extensibility/creating-an-options-page.md). A grade de propriedades Options resultante permite examinar e alterar as propriedades na categoria. Depois de salvar a categoria de propriedade em um arquivo de configurações, você examina o arquivo para ver como os valores da propriedade são armazenados.

## <a name="prerequisites"></a>Pré-requisitos
 A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-settings-category"></a>Criar uma categoria de configurações
 Nesta seção, você usa um ponto de configurações personalizado para salvar e restaurar os valores da categoria configurações.

### <a name="to-create-a-settings-category"></a>Para criar uma categoria de configurações

1. Complete a [página Criar uma opções](../extensibility/creating-an-options-page.md).

2. Abra o arquivo *VSPackage.resx* e adicione esses três recursos de seqüência:

    |Nome|Valor|
    |----------|-----------|
    |106|Minha categoria|
    |107|Minhas Configurações|
    |108|OptionInteger e OptionFloat|

     Isso cria recursos que nomeiam a categoria "Minha categoria", o objeto "Minhas Configurações" e a descrição da categoria "OptionInteger e OptionFloat".

    > [!NOTE]
    > Desses três, apenas o nome da categoria não aparece no assistente **De importações e configurações de exportação.**

3. Em *MyToolsOptionsPackage.cs,* `float` adicione `OptionFloat` uma `OptionPageGrid` propriedade nomeada à classe, como mostrado no exemplo a seguir.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > A `OptionPageGrid` categoria denominada "Minha Categoria" agora `OptionInteger` consiste `OptionFloat`nas duas propriedades, e .

4. Adicione <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a `MyToolsOptionsPackage` à classe e dê-lhe o Nome da categoria "Minha categoria", dê-lhe o Nome do Objeto "Minhas Configurações" e defina isToolsOptionPage como true. Defina a categoriaResourceID, objectNameResourceID e DescriptionResourceID para os IDs de recurso de seqüência correspondentes criados anteriormente.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. Compile o projeto e comece a depuração. No caso experimental, você deve ver que **My Grid Page** agora tem valores inteiros e flutuantes.

## <a name="examine-the-settings-file"></a>Examine o arquivo de configurações
 Nesta seção, você exporta valores de categoria de propriedade para um arquivo de configurações. Você examina o arquivo e, em seguida, importa os valores de volta para a categoria de propriedade.

1. Inicie o projeto no modo de depuração pressionando **F5**. Isso começa a instância experimental.

2. Abra a caixa de diálogo**Opções de** **ferramentas.** > 

3. Na visualização da árvore no painel esquerdo, expanda **Minha Categoria** e clique em My **Grid Page**.

4. Alterar o valor de **OptionFloat** para 3.1416 e **OptionInteger** para 12. Clique em **OK**.

5. No menu, **Ferramentas**, clique em **Importar e Exportar Configurações**.

     O assistente **De importações e configurações de exportação** é exibido.

6. Certifique-se de que **as configurações do ambiente selecionadas de exportação** estão selecionadas e, em seguida, clique **em Avançar**.

     A **página '''''''''''''''''''''''''''**

7. Clique **em Minhas configurações**.

     A **descrição** muda para **OptionInteger e OptionFloat**.

8. Certifique-se de que **Minhas configurações** é a única categoria selecionada e, em seguida, clique **em Next**.

     A **página Nome seu arquivo de configurações** é exibida.

9. Nomeie o arquivo de novas configurações *MySettings.vssettings* e salve-o em um diretório apropriado. Clique em **Concluir**.

     A **página Exportar concluir** informa que suas configurações foram exportadas com sucesso.

10. No menu **Arquivo** , aponte para **Abrir**e clique em **Arquivo**. Localize *MySettings.vssettings* e abra-o.

     Você pode encontrar a categoria de propriedade que você exportou na seção a seguir do arquivo (seus GUIDs diferem).

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     Observe que o nome completo da categoria é formado pela adição de um sublinhado ao nome da categoria seguido pelo nome do objeto. OptionFloat e OptionInteger aparecem na categoria, juntamente com seus valores exportados.

11. Feche o arquivo de configurações sem alterá-lo.

12. No menu **Ferramentas,** clique em **Opções,** **expanda Minha Categoria,** clique em **Minha Página de Grade** e, em seguida, altere o valor de **OptionFloat** para 1.0 e **OptionInteger** para 1. Clique em **OK**.

13. No menu **Ferramentas,** clique em **'Importar e Exportar configurações',** selecione **Importar configurações de ambiente selecionadas**e clique **em 'Avançar**' .

     A **página Salvar configurações de corrente** é exibida.

14. Selecione **Não, basta importar novas configurações** e, em seguida, clique **em Seguir**.

     A **página Escolher uma coleção de configurações para importar** é exibida.

15. Selecione o arquivo *MySettings.vssettings* no nó **Minhas Configurações** da exibição da árvore. Se o arquivo não aparecer na exibição da árvore, clique em **Procurar** e encontrá-lo. Clique em **Próximo**.

     A caixa de diálogo **''''''''''''''''''''''''''''**

16. Certifique-se de que **minhas configurações** estão selecionadas e, em seguida, clique **em Concluir**. Quando a **página Importar concluir** for exibida, clique em **Fechar**.

17. No menu **Ferramentas,** clique em **Opções,** **expanda Minha Categoria,** clique em **Minha Página da Grade** e verifique se os valores da categoria de propriedade foram restaurados.
