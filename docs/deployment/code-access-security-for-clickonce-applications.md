---
title: Segurança de acesso ao código para aplicativos ClickOnce | Microsoft Docs
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
ms.openlocfilehash: 9fd2d9b6792cae002967c9000474a825bd3a0651
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649272"
---
# <a name="code-access-security-for-clickonce-applications"></a>Segurança de acesso do código para aplicativos ClickOnce
Os aplicativos ClickOnce são baseados no Quadro .NET e estão sujeitos a restrições de segurança de acesso ao código. Por essa razão, é importante que você entenda as implicações da segurança de acesso ao código e escreva seus aplicativos ClickOnce de acordo.

 A segurança de acesso a código é um mecanismo no .NET Framework que ajuda a limitar o acesso que o código tem aos recursos e operações protegidas. Você deve configurar as permissões de segurança de acesso ao código para o aplicativo ClickOnce para usar a região apropriada para a localização do instalador do aplicativo. Na maioria dos casos, você pode escolher a região da **Internet** para um conjunto limitado de permissões ou a região **intranet local** para um conjunto maior de permissões.

## <a name="default-clickonce-code-access-security"></a>Segurança de acesso ao código ClickOnce
 Por padrão, um aplicativo ClickOnce recebe permissões de Confiança Total quando ele é instalado ou executado em um computador cliente.

- Um aplicativo que tem permissões de Confiança Total tem acesso irrestrito a recursos como o sistema de arquivos e o registro. Isso potencialmente permite que seu aplicativo (e o sistema do usuário final) seja explorado por código malicioso.

- Quando um aplicativo exige permissões de Confiança Total, o usuário final pode ser solicitado a conceder permissões ao aplicativo. Isso significa que o aplicativo realmente não fornece uma experiência clickOnce, e o prompt pode potencialmente ser confuso para usuários menos experientes.

  > [!NOTE]
  > Ao instalar um aplicativo a partir de mídia removível, como um CD-ROM, o usuário não é solicitado. Além disso, um administrador de rede pode configurar a diretiva de rede para que os usuários não sejam solicitados quando instalam um aplicativo a partir de uma fonte confiável. Para obter mais informações, consulte [visão geral de implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).

  Para restringir as permissões de um aplicativo ClickOnce, você pode modificar as permissões de segurança de acesso ao código para que seu aplicativo solicite a região que melhor se encaixa nas permissões que seu aplicativo exige. Na maioria dos casos, você pode selecionar a região a partir da qual o aplicativo está sendo implantado. Por exemplo, se o aplicativo for um aplicativo corporativo, você pode usar a região **Intranet local.** Se o seu aplicativo for um aplicativo de internet, você pode usar a região da **Internet.**

## <a name="configure-security-permissions"></a>Configurar permissões de segurança
 Você deve sempre configurar seu aplicativo ClickOnce para solicitar a região apropriada para limitar as permissões de segurança de acesso ao código. Você pode configurar permissões de segurança na página **segurança** do **Project Designer**.

 A página **Segurança** no **Project Designer** contém uma caixa de seleção **Habilitar as configurações de segurança Desativada.** Quando esta caixa de seleção é selecionada, solicitações de permissão de segurança são adicionadas ao manifesto de implantação do seu aplicativo. No momento da instalação, o usuário será solicitado a conceder permissões se as permissões solicitadas excederem as permissões padrão para a região da qual o aplicativo é implantado. Para obter mais informações, [consulte Como: Ativar as configurações de segurança ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md).

 Aplicativos implantados em diferentes locais recebem diferentes níveis de permissões sem solicitação. Por exemplo, quando um aplicativo é implantado a partir da Internet, ele recebe um conjunto altamente restritivo de permissões. Quando instalado a partir de uma Intranet local, ele recebe mais permissões e, quando instalado a partir de um CD-ROM, recebe permissões de Confiança Total.

 Como ponto de partida para configurar permissões, você pode selecionar uma região de segurança na lista **Zona** na página **Segurança.** Se sua aplicação for potencialmente implantada em mais de uma região, selecione a região com menos permissões. Para saber mais, veja [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md).

 As propriedades que podem ser definidas variam de acordo com o conjunto de permissões; nem todos os conjuntos de permissões têm propriedades configuráveis. Para obter mais informações sobre a lista completa de <xref:System.Security.Permissions>permissões que seu aplicativo pode solicitar, consulte . Para obter mais informações sobre como definir permissões para uma região personalizada, consulte [Como: Definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

## <a name="debug-an-application-that-has-restricted-permissions"></a>Depurar um aplicativo que tem permissões restritas
 Como desenvolvedor, você provavelmente executará seu computador de desenvolvimento com permissões full trust. Portanto, você não vê as mesmas exceções de segurança quando depura o aplicativo que os usuários podem ver quando executá-lo com permissões restritas.

 Para capturar essas exceções, você tem que depurar o aplicativo com as mesmas permissões que o usuário final. A depuração com permissões restritas pode ser ativada na página **de segurança** do **Project Designer**.

 Quando você depura um aplicativo com permissões restritas, exceções serão levantadas para quaisquer demandas de segurança de código que não tenham sido ativadas na página **de Segurança.** Um ajudante de exceção aparecerá, fornecendo sugestões sobre como modificar seu código para evitar a exceção.

 Além disso, quando você escreve código, o recurso IntelliSense no Editor de código desativará todos os membros que não estão incluídos nas permissões de segurança que você configurou.

 Para obter mais informações, [consulte Como depurar um aplicativo ClickOnce com permissões restritas](securing-clickonce-applications.md).

## <a name="security-permissions-for-browser-hosted-applications"></a>Permissões de segurança para aplicativos hospedados no navegador
 O Visual Studio fornece os seguintes tipos de projeto para aplicativos do Windows Presentation Foundation (WPF):

- Aplicativo WPF Windows

- Aplicativo do navegador WPF

- Biblioteca de Controles Personalizados do WPF

- Biblioteca de Serviços WPF

  Desses tipos de projeto, apenas os aplicativos do Navegador WPF estão hospedados em um navegador da Web e, portanto, exigem configurações especiais de implantação e segurança. As configurações de segurança padrão desses aplicativos são as seguintes:

- **Habilitar as configurações de segurança clickOnce**

- **Este é um aplicativo de confiança parcial**

- **Região de Internet** (com o conjunto de permissões padrão para aplicativos do navegador WPF selecionados)

  Na caixa de diálogo **Configurações avançadas de segurança,** a **depuração deste aplicativo com a** caixa de seleção do conjunto de permissões selecionada é selecionada e desativada. Isso porque o Debug In Zone não pode ser desligado para aplicativos hospedados no navegador.

## <a name="see-also"></a>Confira também
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Como habilitar as configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Como definir uma zona de segurança em um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Como definir permissões personalizadas em um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Como depurar um aplicativo ClickOnce com permissões restritas](securing-clickonce-applications.md)
- [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)
- [Página Segurança, Designer de Projeto](../ide/reference/security-page-project-designer.md)