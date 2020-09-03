---
title: 'Como: criar um controle de caixa de ferramentas que usa Windows Forms | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox control
- winforms
- toolbox
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: 1f3b0c173d5d1f4b3642bf61d2cca9fb6fd231e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850319"
---
# <a name="how-to-create-a-toolbox-control-that-uses-windows-forms"></a>Como criar um controle de caixa de ferramentas que usa o Windows Forms
O modelo de controle de caixa de ferramentas de Windows Forms que está incluído no [!INCLUDE[vssdk_dev11_long](../includes/vssdk-dev11-long-md.md)] permite que você crie Windows Forms controles que são adicionados automaticamente à **caixa de ferramentas** quando a extensão é instalada. Este tópico mostra como usar o modelo para criar um controle de **caixa de ferramentas** que você pode distribuir para outros usuários..  
  
> [!NOTE]
> Para saber como baixar o SDK do Visual Studio, consulte [Visual Studio Extensibility Developer Center](https://msdn.microsoft.com/vsx/default.aspx) no site do MSDN.  
  
## <a name="creating-a-toolbox-control"></a>Criando um controle de caixa de ferramentas  
 Use o modelo de controle caixa de ferramentas de Windows Forms para criar o projeto e, em seguida, crie uma interface do usuário (IU) no designer.  
  
#### <a name="to-create-a-windows-forms-toolbox-control-project"></a>Para criar um projeto de controle de caixa de ferramentas de Windows Forms  
  
1. No menu **Arquivo**, clique em **Novo** e em **Projeto**.  
  
2. Na caixa de diálogo **novo projeto** , em **modelos instalados**, clique no nó para sua linguagem de programação preferida e clique em **extensibilidade**. Na lista de tipos de projeto, selecione **Windows Forms controle caixa de ferramentas**.  
  
3. Na caixa **nome** , digite o nome que você deseja usar para o projeto. Clique em **OK**.  
  
     O Visual Studio cria uma solução que contém um controle de usuário, um atributo para colocar o controle na **caixa de ferramentas**e um manifesto do VSIX para implantação.  
  
#### <a name="to-build-the-control-ui"></a>Para criar a interface do usuário do controle  
  
1. Em **Gerenciador de soluções**, clique duas vezes em ToolboxControl.cs para abri-lo no designer.  
  
2. Na **caixa de ferramentas**, arraste os controles que você deseja para a superfície de design e organize-os de acordo com seu design.  
  
3. Na janela **Propriedades** , defina propriedades públicas no controle de usuário e nos controles filho.  
  
## <a name="coding-the-control"></a>Codificando o controle  
 Por padrão, seu controle aparecerá na **caixa de ferramentas** como **ToolboxControl1** em um grupo de itens da **caixa de ferramentas** que tem o mesmo nome que a sua solução. Você pode alterar esses nomes no arquivo ToolboxControl.cs.  
  
#### <a name="to-code-the-control"></a>Para codificar o controle  
  
1. Em **Gerenciador de soluções**, clique com o botão direito do mouse em ToolboxControl.cs e clique em **Exibir código** para abrir o arquivo na exibição de código.  
  
2. Na definição da classe parcial que implementa o controle, clique com o botão direito do mouse no nome da classe, clique em **Refactor**e, em seguida, clique em **renomear**. Altere o nome da classe para o nome que você deseja exibir na **caixa de ferramentas** quando o controle estiver instalado.  
  
3. Imediatamente acima da definição de classe, na `ProvideToolboxControl` declaração de atributo, altere o valor do primeiro parâmetro para o nome do grupo de itens que hospedará o controle na **caixa de ferramentas**.  
  
     O exemplo a seguir mostra o `ProvideToolboxControl` atributo e a definição de classe ajustada para um controle chamado `Counter` no `General` grupo de itens.  
  
     [!code-csharp[ToolboxControlWinForms#07](../snippets/csharp/VS_Snippets_VSSDK/toolboxcontrolwinforms/cs/toolboxcontrol.cs#07)]  
  
4. Implemente as propriedades, os métodos e os eventos para o controle.  
  
## <a name="building-testing-and-deployment"></a>Criação, teste e implantação  
 Pressionar F5 compila o projeto, que inclui um arquivo de implantação. vsix, e abre uma segunda instância do Visual Studio que tem o controle instalado na **caixa de ferramentas**.  
  
#### <a name="to-build-and-test-the-control"></a>Para compilar e testar o controle  
  
1. Pressione F5.  
  
2. Na nova instância do Visual Studio, crie um projeto de aplicativo Windows Forms.  
  
3. Localize seu controle na **caixa de ferramentas** e arraste-o para a superfície de design.  
  
4. Na janela **Propriedades** , verifique se suas propriedades aparecem conforme o esperado.  
  
5. Adicione qualquer código ou controles adicionais necessários para testar seus métodos e eventos.  
  
6. Pressione F5 para abrir o aplicativo Windows Forms.  
  
7. Verifique se as propriedades, os métodos e os eventos do seu controle se comportam conforme o esperado.  
  
#### <a name="to-deploy-the-control"></a>Para implantar o controle  
  
1. Depois de criar o projeto testado, abra a pasta \bin\debug\ do projeto no explorador de arquivos e localize o arquivo. vsix.  
  
2. Carregue o arquivo. vsix em uma rede ou em um site da Web.  
  
     Se você carregar o arquivo no site da [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , outros usuários poderão usar o **Gerenciador de extensões** no Visual Studio para localizar o controle e instalá-lo.  
  
## <a name="see-also"></a>Consulte Também  
 [Criar um controle de caixa de ferramentas do WPF](../extensibility/creating-a-wpf-toolbox-control.md)
