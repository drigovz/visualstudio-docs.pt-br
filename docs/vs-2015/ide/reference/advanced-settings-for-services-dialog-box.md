---
title: Caixa de diálogo Configurações Avançadas para Serviços | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a021475df1ade9bb6220612aad666d503c19cb8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651715"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Caixa de diálogo Configurações Avançadas para Serviços
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Os serviços de aplicativo cliente fornecem acesso simplificado ao logon, às funções e aos serviços de perfil do [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] por meio dos aplicativos Windows Forms e WPF (Windows Presentation Foundation). É possível usar a página **Serviços** no **Designer de Projeto** para configurar serviços de aplicativo cliente. Para obter mais informações sobre a página **Serviços**, consulte [Página Serviços, Designer de Projeto](../../ide/reference/services-page-project-designer.md).

 Use a caixa de diálogo **Configurações Avançadas para Serviços** da página **Serviços** no **Designer de Projeto** para definir configurações avançadas para serviços de aplicativo cliente. Ao usar essas configurações, é possível substituir alguns comportamentos padrão do serviço de aplicativo para habilitar cenários menos comuns. Para obter mais informações, consulte [Serviços de aplicativo cliente](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).

 Para acessar a caixa de diálogo **Configurações Avançadas para Serviços**, selecione um nó do projeto no **Gerenciador de Soluções** e, em seguida, clique em **Propriedades** no menu **Projeto**. Quando o **Designer de Projeto** for exibido, clique na guia **Serviços** e, em seguida, no botão **Avançado**. Esse botão só será desabilitado quando você habilitar os serviços de aplicativo cliente.

## <a name="task-list"></a>Lista de Tarefas
 [Como configurar serviços de aplicativo cliente](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)

 [Como trabalhar offline com serviços de aplicativo cliente](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Salvar hash de senha localmente para habilitar logon offline** Especifica se um formato criptografado da senha do usuário será armazenado em cache localmente para permitir que o usuário faça logon quando o aplicativo estiver no modo offline. Para obter mais informações, consulte [Como trabalhar offline com serviços de aplicativo cliente](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Essa opção é habilitada por padrão.

 **Exigir que os usuários façam logon novamente sempre que o cookie do servidor expirar** Especifica se os usuários já autenticados serão reautenticados automaticamente quando o aplicativo acessar as funções ou o serviço de perfil e o cookie de autenticação do servidor tiver expirado. Selecione essa opção para negar acesso aos serviços de aplicativo e exigir a reautenticação explícita depois que o cookie expirar. Isso é útil para aplicativos implantados em locais públicos, para garantir que os usuários que deixam o aplicativo em execução após o uso não permanecerão autenticados por tempo indefinido. Essa opção é desmarcada por padrão.

 **Tempo limite do cache de serviço de função** Especifica o tempo de duração em que o provedor de função do cliente usará os valores de função armazenados em cache em vez de acessar o serviço de funções. Defina esse intervalo de tempo como um valor pequeno quando as funções forem atualizadas com frequência ou como um valor maior quando as funções forem raramente atualizadas. O valor padrão é um dia.

 O provedor de função acessa os valores de função em cache ou o serviço de funções quando você chama o método <xref:System.Web.Security.RolePrincipal.IsInRole%2A>. Para limpar o cache de forma programática e forçar esse método a acessar o serviço remoto, chame o método <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.

 **Usar cadeia de conexão personalizada** Especifica se os provedores de serviço do cliente usarão um armazenamento de dados personalizado para o cache local. Por padrão, os provedores de serviço usarão o sistema de arquivos local para o cache. A seleção desta opção populará automaticamente a caixa de texto com uma cadeia de conexão padrão. É possível manter a cadeia de conexão padrão para gerar automaticamente e usar um banco de dados SQL Server Compact Edition ou é possível especificar uma cadeia de conexão para um banco de dados SQL Server existente. Para obter mais informações, consulte [Como configurar serviços de aplicativo cliente](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). Essa opção é desmarcada por padrão.

## <a name="see-also"></a>Consulte Também
 [Client Application Services](https://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e) [Página de serviços de serviços de aplicativos de cliente, designer de projeto](../../ide/reference/services-page-project-designer.md) [como: configurar o cliente serviços de aplicativos](https://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8) [como trabalhar offline com o cliente serviços de aplicativos](https://msdn.microsoft.com/f792cb16-8520-4a0f-9dc9-07bfbc454e38)
