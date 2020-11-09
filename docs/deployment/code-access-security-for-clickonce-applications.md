---
title: Segurança de acesso a código para aplicativos ClickOnce | Microsoft Docs
description: Saiba mais sobre a segurança de acesso do código para aplicativos ClickOnce e como configurar as permissões de segurança de acesso ao código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 256a41138a3918dd61d8fd496465bb0230fb9362
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382566"
---
# <a name="code-access-security-for-clickonce-applications"></a>Segurança de acesso do código para aplicativos ClickOnce
Os aplicativos ClickOnce são baseados na .NET Framework e estão sujeitos a restrições de segurança de acesso ao código. Por esse motivo, é importante entender as implicações da segurança de acesso ao código e escrever seus aplicativos ClickOnce de forma adequada.

 A segurança de acesso ao código é um mecanismo no .NET Framework que ajuda a limitar o acesso que o código tem a recursos e operações protegidos. Você deve configurar as permissões de segurança de acesso do código para seu aplicativo ClickOnce para usar a zona apropriada para o local do instalador do aplicativo. Na maioria dos casos, você pode escolher a zona da **Internet** para um conjunto limitado de permissões ou a zona **da intranet local** para um conjunto maior de permissões.

## <a name="default-clickonce-code-access-security"></a>Segurança de acesso de código ClickOnce padrão
 Por padrão, um aplicativo ClickOnce recebe permissões de confiança total quando ele é instalado ou executado em um computador cliente.

- Um aplicativo que tem permissões de confiança total tem acesso irrestrito a recursos como o sistema de arquivos e o registro. Isso potencialmente permite que seu aplicativo (e o sistema do usuário final) seja explorado por código mal-intencionado.

- Quando um aplicativo requer permissões de confiança total, o usuário final pode ser solicitado a conceder permissões ao aplicativo. Isso significa que o aplicativo não fornece realmente uma experiência ClickOnce, e o prompt pode potencialmente confundir com usuários menos experientes.

  > [!NOTE]
  > Ao instalar um aplicativo de mídia removível, como um CD-ROM, o usuário não será solicitado. Além disso, um administrador de rede pode configurar a diretiva de rede para que os usuários não sejam solicitados quando instalarem um aplicativo de uma fonte confiável. Para obter mais informações, consulte [visão geral da implantação de aplicativo confiável](../deployment/trusted-application-deployment-overview.md).

  Para restringir as permissões para um aplicativo ClickOnce, você pode modificar as permissões de segurança de acesso ao código do seu aplicativo para solicitar a zona que melhor se adapta às permissões que seu aplicativo requer. Na maioria dos casos, você pode selecionar a zona da qual o aplicativo está sendo implantado. Por exemplo, se seu aplicativo for um aplicativo empresarial, você poderá usar a zona **da intranet local** . Se seu aplicativo for um aplicativo de Internet, você poderá usar a zona da **Internet** .

## <a name="configure-security-permissions"></a>Configurar permissões de segurança
 Você sempre deve configurar seu aplicativo ClickOnce para solicitar a zona apropriada para limitar as permissões de segurança de acesso ao código. Você pode configurar permissões de segurança na página **segurança** do **Designer de projeto**.

 A página **segurança** no **Designer de projeto** contém uma caixa de seleção **Habilitar configurações de segurança do ClickOnce** . Quando essa caixa de seleção está marcada, as solicitações de permissão de segurança são adicionadas ao manifesto de implantação para seu aplicativo. No momento da instalação, o usuário receberá uma solicitação para conceder permissões se as permissões solicitadas excederem as permissões padrão para a zona a partir da qual o aplicativo é implantado. Para obter mais informações, consulte [como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).

 Os aplicativos implantados de diferentes locais recebem diferentes níveis de permissões sem solicitação. Por exemplo, quando um aplicativo é implantado pela Internet, ele recebe um conjunto de permissões altamente restritivo. Quando instalado de uma intranet local, ele recebe mais permissões e, quando instalado a partir de um CD-ROM, ele recebe permissões de confiança total.

 Como ponto de partida para configurar permissões, você pode selecionar uma zona de segurança na lista **zona** na página **segurança** . Se seu aplicativo potencialmente será implantado de mais de uma zona, selecione a zona com o mínimo de permissões. Para saber mais, veja [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).

 As propriedades que podem ser definidas variam de acordo com o conjunto de permissões; Nem todos os conjuntos de permissões têm propriedades configuráveis. Para obter mais informações sobre a lista completa de permissões que seu aplicativo pode solicitar, consulte <xref:System.Security.Permissions> . Para obter mais informações sobre como definir permissões para uma zona personalizada, consulte [como: definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

## <a name="debug-an-application-that-has-restricted-permissions"></a>Depurar um aplicativo que tenha permissões restritas
 Como desenvolvedor, você provavelmente executou seu computador de desenvolvimento com permissões de confiança total. Portanto, você não vê as mesmas exceções de segurança ao depurar o aplicativo que os usuários podem ver quando executam com permissões restritas.

 Para capturar essas exceções, você precisa depurar o aplicativo com as mesmas permissões que o usuário final. A depuração com permissões restritas pode ser habilitada na página **segurança** do **Designer de projeto**.

 Quando você depura um aplicativo com permissões restritas, exceções serão geradas para qualquer demanda de segurança de código que não tenha sido habilitada na página **segurança** . Um auxiliar de exceção será exibido, fornecendo sugestões sobre como modificar seu código para evitar a exceção.

 Além disso, quando você escreve o código, o recurso IntelliSense no editor de código desabilitará todos os membros que não estão incluídos nas permissões de segurança que você configurou.

 Para obter mais informações, consulte [como: Depurar um aplicativo ClickOnce com permissões restritas](securing-clickonce-applications.md).

## <a name="security-permissions-for-browser-hosted-applications"></a>Permissões de segurança para aplicativos hospedados em navegador
 O Visual Studio fornece os seguintes tipos de projeto para aplicativos Windows Presentation Foundation (WPF):

- Aplicativo WPF Windows

- Aplicativo de navegador da Web do WPF

- Biblioteca de Controles Personalizados do WPF

- Biblioteca de serviços do WPF

  Desses tipos de projeto, somente os aplicativos de navegador da Web do WPF são hospedados em um navegador da Web e, portanto, exigem configurações especiais de implantação e segurança. As configurações de segurança padrão para esses aplicativos são as seguintes:

- **Habilitar configurações de segurança do ClickOnce**

- **Este é um aplicativo de confiança parcial**

- **Zona da Internet** (com o conjunto de permissões padrão para aplicativos do navegador da Web do WPF selecionados)

  Na caixa de diálogo **configurações de segurança avançadas** , a caixa de seleção **depurar este aplicativo com o conjunto de permissões selecionado** está marcada e desabilitada. Isso ocorre porque a depuração na zona não pode ser desativada para aplicativos hospedados em navegador.

## <a name="see-also"></a>Confira também
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Como habilitar as configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Como definir uma zona de segurança em um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Como definir permissões personalizadas em um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Como depurar um aplicativo ClickOnce com permissões restritas](securing-clickonce-applications.md)
- [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)
- [Página Segurança, Designer de Projeto](../ide/reference/security-page-project-designer.md)