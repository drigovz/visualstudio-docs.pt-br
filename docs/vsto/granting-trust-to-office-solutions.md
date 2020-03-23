---
title: Conceder confiança às soluções do Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303298"
---
# <a name="grant-trust-to-office-solutions"></a>Conceder confiança às soluções do Office
  Conceder confiança às soluções do Office significa modificar a política de segurança de cada computador alvo para confiar na montagem da solução, manifesto de aplicativo, manifesto de implantação e documento. A confiança pode ser concedida à solução do Office por você ou pelo usuário final.

 Você pode conceder total confiança à solução do Office assinando os manifestos de solicitação e implantação.

 Os usuários finais podem conceder confiança à solução [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] do Office tomando uma decisão de confiança no prompt de confiança.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>Confie na solução assinando os manifestos de aplicação e implantação
 Todos os manifestos de aplicação e implantação para soluções do Office devem ser assinados com um certificado que identifique o editor. Os certificados fornecem uma base para tomar decisões de confiança.

 Um certificado temporário é criado para você e concedido confiança no momento da compilação para que a solução seja executada enquanto você depura-lo. Se você publicar uma solução assinada com um certificado temporário, o usuário final será solicitado a tomar uma decisão de confiança.

 Se você assinar a solução com um certificado conhecido e confiável, a solução será instalada automaticamente sem solicitar ao usuário final que tome uma decisão de confiança. Para obter mais informações sobre como obter um certificado para assinatura, consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Depois que um certificado é obtido, o certificado deve ser explicitamente confiável adicionando-o à lista Trusted Publishers. Para obter mais informações, consulte [Como: Adicionar um editor confiável a um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Se um desenvolvedor assinar a solução com um certificado temporário, um administrador poderá reassinar a personalização com um certificado conhecido e confiável usando a Ferramenta de Geração e Edição de Manifestos *(mage.exe),* que é uma das ferramentas microsoft .NET Framework. Para obter mais informações sobre como assinar soluções, consulte [Como: Assinar soluções do Office](../vsto/how-to-sign-office-solutions.md) e [Como: Assinar manifestos de aplicação e implantação.](../ide/how-to-sign-application-and-deployment-manifests.md)

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>Confie na solução usando o prompt de confiança ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]solicita ao usuário final que tome a decisão de confiança se não houver uma política em toda a organização que confie no certificado da solução. Se o usuário final conceder confiança à solução, será criada uma entrada na lista de inclusão que contém uma URL e uma chave pública para armazenar essa decisão de confiança. Quando uma personalização confiável é executada mais tarde, o usuário final não é solicitado novamente.

 Os administradores [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] podem desativar o prompt de confiança ou exigir que o prompt ocorra apenas para soluções que estejam assinadas com um certificado Authenticode. Para obter mais informações sobre como alterar essas configurações para as regiões MyComputer, LocalIntranet, Internet, TrustedSites e UntrustedSites, consulte [Como: Configurar o comportamento de prompt de confiança do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Confira também

- [Soluções do Secure Office](../vsto/securing-office-solutions.md)
- [Conceder confiança aos documentos](../vsto/granting-trust-to-documents.md)
- [Solucionar problemas segurança da solução do Office](../vsto/troubleshooting-office-solution-security.md)
- [Considerações específicas de segurança para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md)