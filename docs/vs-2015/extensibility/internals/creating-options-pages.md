---
title: Criando páginas de opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c2b993a6c6947adfa3b01f2947b992b23236b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196939"
---
# <a name="creating-options-pages"></a>Criando páginas de opções
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Na [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] estrutura de pacote gerenciado, as classes derivadas de <xref:Microsoft.VisualStudio.Shell.DialogPage> estender o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE adicionando as páginas de **Opções** no menu **ferramentas** .  
  
 Um objeto que implementa uma determinada página de **opção de ferramentas** é associado a VSPackages específicos pelo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> objeto.  
  
 Como o ambiente cria uma instância do objeto que implementa uma página de **Opções de ferramentas** em particular quando essa página específica é exibida pelo IDE:  
  
- Uma página de **Opções de ferramentas** deve ser implementada em seu próprio objeto e não no objeto que implementa um VSPackage.  
  
- Um objeto não pode implementar várias páginas de **Opções de ferramentas** .  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Registrando como um provedor de páginas de opções de ferramentas  
 Um VSPackage que dá suporte à configuração de usuário por meio das páginas de **Opções de ferramentas** indica os objetos que fornecem as páginas de **Opções de ferramentas** aplicando instâncias do <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> aplicadas à <xref:Microsoft.VisualStudio.Shell.Package> implementação.  
  
 Deve haver uma instância do <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para cada <xref:Microsoft.VisualStudio.Shell.DialogPage> tipo derivado que implemente uma página de **Opções de ferramentas** .  
  
 Cada instância do <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> usa o tipo que implementa a página **Opções de ferramentas** , cadeias de caracteres que contêm a categoria e a subcategoria usadas para identificar uma página de opções de **ferramentas** e informações de recurso para registrar o tipo como fornecendo uma página de **Opções de ferramentas** .  
  
## <a name="persisting-tools-options-page-state"></a>Opções das ferramentas de persistência estado da página  
 Se uma implementação de página de **Opções de ferramentas** estiver registrada com o suporte de automação habilitado, o IDE persiste o estado da página junto com todas as outras páginas de **Opções de ferramentas** .  
  
 Um VSPackage pode gerenciar sua própria persistência usando o <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . Somente um ou outro método de persistência deve ser usado.  
  
## <a name="implementing-dialogpage-class"></a>Implementando classe DialogPage  
 Um objeto que fornece a implementação de um tipo derivado de um VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage> pode aproveitar os seguintes recursos herdados:  
  
- Uma janela de interface do usuário padrão.  
  
- Um mecanismo de persistência padrão disponível se <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> for aplicado à classe ou se a <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> propriedade for definida como `true` para o <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> que é aplicado à classe.  
  
- Suporte à automação.  
  
  O requisito mínimo para um objeto que implementa uma página de **Opções de ferramentas** usando <xref:Microsoft.VisualStudio.Shell.DialogPage> é a adição de propriedades públicas.  
  
  Se a classe estiver devidamente registrada como um provedor de páginas de **Opções de ferramentas** , suas propriedades públicas estarão disponíveis na seção **Opções** do menu **ferramentas** na forma de uma grade de propriedades.  
  
  Todos esses recursos padrão podem ser substituídos. Por exemplo, para criar uma interface de usuário mais sofisticada, é necessário substituir apenas a implementação padrão do <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> .  
  
## <a name="example"></a>Exemplo  
 O que vem a seguir é uma implementação simples de "Olá mundo" de uma página de opções. Adicionar o código a seguir a um projeto padrão criado pelo modelo de pacote do Visual Studio com a opção de **comando de menu** selecionada irá demonstrar adequadamente a funcionalidade da página de opções.  
  
### <a name="description"></a>Descrição  
 A classe a seguir define uma página de opções mínima "Olá, mundo". Quando aberto, o usuário pode definir a `HelloWorld` propriedade pública em uma grade de propriedades.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Descrição  
 Aplicar o atributo a seguir à classe de pacote disponibiliza a página opções quando o pacote é carregado. Os números são IDs de recursos arbitrários para a categoria e a página, e o valor booliano no final especifica se a página oferece suporte à automação.  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Descrição  
 O manipulador de eventos a seguir exibe um resultado, dependendo do valor do conjunto de propriedades na página opções. Ele usa o <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> método com o resultado convertido explicitamente no tipo de página de opção personalizada para acessar as propriedades expostas pela página.  
  
 No caso de um projeto gerado pelo modelo de pacote, chame essa função da `MenuItemCallback` função para anexá-la ao comando padrão adicionado ao menu **ferramentas** .  
  
### <a name="code"></a>Código  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>Consulte Também  
 [Estendendo configurações e opções de usuário](../../extensibility/extending-user-settings-and-options.md)   
 [Suporte à automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md)
