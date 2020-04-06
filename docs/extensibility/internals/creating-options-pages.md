---
title: Criando páginas de opções | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709148"
---
# <a name="create-options-pages"></a>Criar páginas de opções
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estrutura de pacotes gerenciados, <xref:Microsoft.VisualStudio.Shell.DialogPage> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] as classes derivadas de estender o IDE adicionando páginas **de opções** no menu **Ferramentas.**

 Um objeto que implementa uma determinada página de opção <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> de **ferramentas** está associado a VSPackages específicos pelo objeto.

 Como o ambiente instancia o objeto que implementa uma página de **opções** de ferramentas específicas quando essa página em particular é exibida pelo IDE:

- Uma página **de opção de ferramentas** deve ser implementada em seu próprio objeto, e não no objeto que implementa um VSPackage.

- Um objeto não pode implementar várias **páginas de opções de** ferramentas.

## <a name="register-as-a-tools-options-page-provider"></a>Registre-se como um provedor de página de opções de ferramentas
 Um VSPackage que suporta a configuração do usuário através de páginas **de opções de ferramentas** indica os objetos que fornecem essas páginas de **opções de** <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> ferramentas aplicando instâncias aplicadas à <xref:Microsoft.VisualStudio.Shell.Package> implementação.

 Deve haver uma <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> instância <xref:Microsoft.VisualStudio.Shell.DialogPage>de para cada tipo derivado que implemente uma página **de Opções de Ferramentas.**

 Cada instância <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> de uso usa o tipo que implementa a página **Opções de ferramentas,** strings que contêm a categoria e a subcategoria usadas para identificar uma página **de Opções de ferramentas** e informações de recursos para registrar o tipo como fornecendo uma página **Opções de Ferramentas.**

## <a name="persist-tools-options-page-state"></a>Persist Apágina de opções de ferramentas
 Se a implementação de uma página **de opções de ferramentas** for registrada com suporte à automação ativado, o IDE persistirá o estado da página, juntamente com todas as outras páginas de **Opções de Ferramentas.**

 Um VSPackage pode gerenciar sua <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>própria persistência usando . Apenas um ou outro método de persistência deve ser utilizado.

## <a name="implement-dialogpage-class"></a>Implementar a classe DiálogoPágina
 Um objeto que fornece a implementação de um tipo derivado de um <xref:Microsoft.VisualStudio.Shell.DialogPage>VSPackage pode tirar proveito dos seguintes recursos herdados:

- Uma janela de interface de usuário padrão.

- Um mecanismo de persistência <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> padrão disponível se for aplicado <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> à classe `true` ou <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> se a propriedade for definida para o que é aplicado à classe.

- Suporte à automação.

  O requisito mínimo para um objeto implementar uma página **de opções de ferramentas** usando <xref:Microsoft.VisualStudio.Shell.DialogPage> é a adição de propriedades públicas.

  Se a classe estiver devidamente registrada como provedor a página **Opções de Ferramentas,** suas propriedades públicas estiverem disponíveis na seção **Opções** do menu **Ferramentas** na forma de uma grade de propriedades.

  Todos esses recursos padrão podem ser substituídos. Por exemplo, para criar uma interface de usuário mais <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>sofisticada requer apenas a substituição da implementação padrão de .

## <a name="example"></a>Exemplo
 O que se segue é uma simples implementação "Hello world" de uma página de opções. Adicionar o seguinte código a um projeto padrão criado pelo modelo de pacote do Visual Studio com a opção **Menu Command** selecionada demonstrará adequadamente a funcionalidade da página de opção.

### <a name="description"></a>Descrição
 A classe a seguir define uma página mínima de opções "Hello world". Quando aberto, o usuário `HelloWorld` pode definir o imóvel público em uma grade de propriedade.

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>Descrição
 A aplicação do seguinte atributo à classe do pacote torna a página de opções disponível quando o pacote é carregado. Os números são IDs de recursos arbitrários para a categoria e a página, e o valor booleano no final especifica se a página suporta automação.

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>Descrição
 O manipulador de eventos a seguir exibe um resultado dependendo do valor da propriedade definida na página de opções. Ele usa <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> o método com o resultado explicitamente lançado no tipo de página de opção personalizada para acessar as propriedades expostas pela página.

 No caso de um projeto gerado pelo modelo do `MenuItemCallback` pacote, chame essa função da função para anexá-la ao comando padrão adicionado ao menu **Ferramentas.**

### <a name="code"></a>Código
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>Confira também
- [Estender as configurações e opções do usuário](../../extensibility/extending-user-settings-and-options.md)
- [Suporte à automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md)
