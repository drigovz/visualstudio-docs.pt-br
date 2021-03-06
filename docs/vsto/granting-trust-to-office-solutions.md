---
title: Conceder confiança às soluções do Office
description: Para conceder confiança às soluções do Office significa modificar a política de segurança de cada computador de destino para confiar no assembly da solução, no manifesto de implantação e no documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f98f3154a0708ce7a01603968f0f5774dd86f40e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910235"
---
# <a name="grant-trust-to-office-solutions"></a>Conceder confiança às soluções do Office
  Conceder confiança a soluções do Office significa modificar a política de segurança de cada computador de destino para confiar no assembly da solução, manifesto do aplicativo, manifesto de implantação e documento. A confiança pode ser concedida à solução do Office por você ou pelo usuário final.

 Você pode conceder confiança total à solução do Office assinando os manifestos de implantação e de aplicativo.

 Os usuários finais podem conceder confiança à solução do Office, fazendo uma decisão de confiança no [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt de confiança.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> Confiar na solução assinando os manifestos de implantação e de aplicativo
 Todos os manifestos de aplicativo e implantação para soluções do Office devem ser assinados com um certificado que identifica o Publicador. Os certificados fornecem uma base para tomar decisões de confiança.

 Um certificado temporário é criado para você e recebe confiança no momento da compilação para que a solução seja executada enquanto você a depura. Se você publicar uma solução que é assinada com um certificado temporário, o usuário final será solicitado a tomar uma decisão de confiança.

 Se você assinar a solução com um certificado conhecido e confiável, a solução será instalada automaticamente sem solicitar que o usuário final tome uma decisão de confiança. Para obter mais informações sobre como obter um certificado para assinatura, consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Depois que um certificado é obtido, o certificado deve ser explicitamente confiável ao adicioná-lo à lista de editores confiáveis. Para obter mais informações, consulte [como: adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Se um desenvolvedor assinar a solução com um certificado temporário, um administrador poderá assinar novamente a personalização com um certificado conhecido e confiável usando o Manifest Generation and Editing Tool (*mage.exe*), que é uma das ferramentas do Microsoft .NET Framework. Para obter mais informações sobre soluções de assinatura, consulte [como: assinar soluções do Office](../vsto/how-to-sign-office-solutions.md) e [como assinar manifestos de aplicativo e implantação](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Confiar na solução usando o prompt de confiança do ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] solicita que o usuário final tome a decisão de confiança se não houver nenhuma política de toda a organização que confie no certificado da solução. Se o usuário final conceder confiança à solução, será criada uma entrada da lista de inclusão que contém uma URL e uma chave pública para armazenar essa decisão de confiança. Quando uma personalização confiável é executada mais tarde, o usuário final não é solicitado novamente.

 Os administradores podem desabilitar o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt de confiança ou exigir que o prompt ocorra somente para soluções assinadas com um certificado Authenticode. Para obter mais informações sobre como alterar essas configurações para as zonas MyComputer, LocalIntranet, Internet, TrustedSites e UntrustedSites, consulte [como configurar o comportamento do prompt de confiança do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Consulte também

- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
- [Conceder confiança aos documentos](../vsto/granting-trust-to-documents.md)
- [Solucionar problemas de segurança da solução do Office](../vsto/troubleshooting-office-solution-security.md)
- [Considerações de segurança específicas para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md)