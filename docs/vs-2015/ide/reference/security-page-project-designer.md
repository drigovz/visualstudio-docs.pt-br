---
title: Página Segurança, Designer de Projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 768b0d43d8e6b52781e3f2dc2029e0b96b3a6548
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665534"
---
# <a name="security-page-project-designer"></a>Página Segurança, Designer de Projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A página **Segurança** do **Designer de Projeto** é usada para definir configurações de segurança de acesso do código para aplicativos implantados usando a implantação do [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)]. Para obter mais informações, consulte [segurança de acesso de código para aplicativos ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Para acessar a página **Segurança**, clique em um nó do projeto no **Gerenciador de Soluções** e, em seguida, no menu **Projeto**, clique em **Propriedades**. Quando o **Designer de Projeto** for exibido, clique na guia **Segurança**.

## <a name="security-settings"></a>Configurações de segurança
 **Habilitar configurações de segurança do ClickOnce** Determina se as configurações de segurança estão habilitadas em tempo de design. Quando esta opção estiver desmarcada, todas as outras opções na página **Segurança** não ficarão disponíveis.

> [!NOTE]
> Quando você publica um aplicativo usando o assistente **Publicar**, essa opção fica habilitada automaticamente.

 Quando seleciona a opção, você tem a escolha de selecionar um de dois botões de opção: **Este é um aplicativo de confiança total** ou **Este é um aplicativo de confiança parcial**.

 Por padrão, para projetos de Aplicativo de navegador da Web do WPF, essa opção fica selecionada.

 Por padrão, para todos os outros tipos de projeto, a opção fica desmarcada.

 **Este é um aplicativo de confiança total** Se você selecionar essa opção, o aplicativo solicitará permissões de confiança total quando for instalado ou executado em um computador cliente. Evite usar a Confiança Total, se possível, porque o aplicativo receberá acesso irrestrito a recursos como o sistema de arquivos e o Registro.

 Por padrão, para projetos de Aplicativo de navegador da Web do WPF, essa opção fica definida como Confiança parcial.

 Por padrão, para todos os outros tipos de projeto, a opção fica definida como Confiança Total.

 **Este é um aplicativo de confiança parcial** Se você selecionar essa opção, o aplicativo solicitará permissões de confiança parcial quando for instalado ou executado em um computador cliente. *Confiança parcial* significa que somente as ações permitidas de acordo com as permissões de segurança de acesso de código solicitadas serão executadas. Para obter mais informações sobre como configurar permissões de segurança, consulte [Segurança de acesso do código para aplicativos ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Você pode especificar as configurações de segurança de Confiança parcial configurando as opções na área **Permissões de Segurança do ClickOnce**.

## <a name="clickonce-security-permissions"></a>Permissões de Segurança do ClickOnce
 **Zona em que o aplicativo será instalado** Especifica um conjunto padrão de permissões de segurança de acesso ao código. Escolha **Internet** ou **Intranet Local** para um conjunto de permissões restritas, ou escolha **(Personalizado)** para configurar um conjunto de permissões personalizadas. Se o aplicativo solicitar mais permissões do que aquelas que são concedidas em uma zona, um prompt de confiança do ClickOnce será exibido para o usuário final conceder as permissões adicionais. Para obter mais informações sobre como configurar permissões de segurança, consulte [Segurança de acesso do código para aplicativos ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).

 Por padrão, para projetos de Aplicativo de navegador da Web do WPF, essa opção fica definida como **Internet**.

 **Editar XML de permissões** Abre o modelo de manifesto do aplicativo (App. manifest) para configurar as permissões para o conjunto de permissões **(personalizado)** .

 **Avançado** Abre a [caixa de diálogo Configurações de segurança avançadas](../../ide/reference/advanced-security-settings-dialog-box.md), que é usada para definir as configurações para depurar o aplicativo com permissões restritas. Essas configurações são verificadas durante a depuração, e exceções de permissão indicam que seu aplicativo pode precisar de mais permissões do que as que foram definidas em uma zona.

## <a name="see-also"></a>Consulte Também
 <xref:System.Security.Permissions.WebBrowserPermission> <xref:System.Security.Permissions.MediaPermission>
 [Segurança de acesso a código para aplicativos ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md) [como: Habilitar configurações de segurança do ClickOnce](../../deployment/how-to-enable-clickonce-security-settings.md) [como: definir uma zona de segurança para um aplicativo ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md) [como: definir permissões personalizadas para um aplicativo ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md) [como depurar um aplicativo ClickOnce com permissões restritas](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [Propriedades do projeto](../../ide/reference/project-properties-reference.md) de [implantação e segurança](../../deployment/clickonce-security-and-deployment.md) [configuração da caixa de diálogo Configurações avançadas de segurança](../../ide/reference/advanced-security-settings-dialog-box.md)
