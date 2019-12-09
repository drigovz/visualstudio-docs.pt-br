---
title: Segurança para soluções do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6dc1449a40528670274ea5b275cca3f0a8d2f277
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983785"
---
# <a name="security-for-sharepoint-solutions"></a>Segurança para soluções do SharePoint
  o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incorpora os seguintes recursos para ajudar a aprimorar a segurança dos aplicativos do SharePoint.

## <a name="safe-control-entries"></a>Entradas de controle seguro
 Cada item de projeto do SharePoint criado no [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] tem uma propriedade de **entradas de controle segura** que representa uma coleção de controles seguros. Seu subpropriedade **seguro** permite que você especifique os controles que você considera seguros. Para obter mais informações, consulte [fornecer informações de pacote e de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [especificar Web Parts seguras](/previous-versions/office/developer/sharepoint2003/dd583154(v=office.11)#specifying-safe-web-parts).

## <a name="allowpartiallytrustedcallers-attribute"></a>Atributo AllowPartiallyTrustedCallers
 Por padrão, somente os aplicativos que são totalmente confiáveis pelo sistema de segurança de acesso ao código (CAS) do Runtime podem acessar um assembly de código gerenciado compartilhado. Marcar um assembly totalmente confiável com o atributo AllowPartiallyTrustedCallers permite que os assemblies parcialmente confiáveis o acessem.

 O atributo AllowPartiallyTrustedCallers é adicionado a qualquer solução do SharePoint que não esteja implantada no cache de assembly global do sistema ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). Isso inclui soluções em área restrita ou soluções implantadas no diretório bin do aplicativo do SharePoint. Para obter mais informações, consulte [as alterações de segurança da versão 1 para a estrutura de Microsoft .net](/previous-versions/msp-n-p/ff921345(v=pandp.10)) e [implantação de Web Parts no SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

## <a name="safe-against-script-property"></a>Seguro contra propriedade de script
 A *injeção de script* é a inserção de código potencialmente mal-intencionado em controles ou páginas da Web. Para ajudar a proteger sites do SharePoint 2010 contra injeção de script, os colaboradores não podem exibir ou editar Web Parts ou suas propriedades por padrão. Esse comportamento é controlado por um atributo SafeControl chamado SafeAgainstScript. Em [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)], defina este atributo em **entradas de controle seguro** do item de projeto subpropriedade **Safe contra script**. Para obter mais informações, consulte [fornecer informações de pacote e de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) e [como marcar controles como controles seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md).

## <a name="vista-and-windows-7-user-account-control"></a>Controle de conta de usuário do vista e do Windows 7
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporar um recurso de segurança conhecido como UAC (controle de conta de usuário). Para desenvolver soluções do SharePoint em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] em sistemas [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], o UAC requer que você execute [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como administrador do sistema. No menu **Iniciar** , abra o menu de atalho para [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e, em seguida, escolha **Executar como administrador**.

 Para configurar o atalho [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para sempre executar como administrador, abra o menu de atalho, escolha **Propriedades**, escolha o botão **avançado** na caixa de diálogo **Propriedades** e marque a caixa de seleção **Executar como administrador** .

 Para obter mais informações, consulte [compreendendo e Configurando o controle de conta de usuário no Windows Vista](/previous-versions/windows/it-pro/windows-vista/cc709628(v=ws.10)). e o [controle de conta de usuário do Windows 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731416(v=ws.10)).

## <a name="sharepoint-permissions-considerations"></a>Considerações sobre permissões do SharePoint
 Para desenvolver soluções do SharePoint, você deve ter permissões suficientes para executar e depurar soluções do SharePoint. Para poder testar uma solução do SharePoint, execute as seguintes etapas para garantir que você tenha as permissões necessárias:

1. Adicione sua conta de usuário como administrador no sistema.

2. Adicione sua conta de usuário como um administrador de farm para o servidor do SharePoint.

    1. Na administração central do SharePoint 2010, escolha o link **gerenciar o grupo Administradores de farm** .

    2. Na página **Administradores de farm** , escolha a opção de menu **novo**

3. Adicione sua conta de usuário ao para o grupo de WSS_ADMIN_WPG.

## <a name="additional-security-resources"></a>Recursos de segurança adicionais
 Para obter mais informações sobre problemas de segurança, consulte o seguinte.

### <a name="visual-studio-security"></a>Segurança do Visual Studio

- [Segurança e permissões de usuário](/previous-versions/visualstudio/visual-studio-2010/ms165099(v=vs.100))

- [Segurança em código nativo e .NET Framework](/previous-versions/visualstudio/visual-studio-2010/1787tk12(v=vs.100))

- [Segurança no .NET Framework](/previous-versions/dotnet/netframework-4.0/fkytk30f(v=vs.100))

### <a name="sharepoint-security"></a>Segurança do SharePoint

- [Administração e segurança do SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee537811(v=office.14))

- [Central de recursos de segurança do SharePoint](/sharepoint/dev/)

- [Protegendo Web Parts no SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768613(v=office.14))

- [Melhorando a segurança de aplicativos Web: ameaças e contramedidas](/previous-versions/msp-n-p/ff649874(v=pandp.10))

### <a name="general-security"></a>Segurança geral

- [Ciclo de vida de desenvolvimento de segurança do MSDN](https://www.microsoft.com/msrc?rtc=1)

- [Criando aplicativos ASP.NET seguros: autenticação, autorização e comunicação segura](/previous-versions/msp-n-p/ff649100(v=pandp.10))

## <a name="see-also"></a>Consulte também

- [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)