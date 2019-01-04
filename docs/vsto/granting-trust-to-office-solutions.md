---
title: Conceder confiança a soluções do Office
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1acc6f73dd52bacdfd62aff3b2da62e559c4fda6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890463"
---
# <a name="grant-trust-to-office-solutions"></a>Conceder confiança a soluções do Office
  Conceder confiança para o meio de soluções Office modificando a política de segurança de cada computador de destino para o assembly da solução, o manifesto do aplicativo, o manifesto de implantação e o documento de confiança. Relação de confiança pode ser concedida a solução do Office por você ou o usuário final.

 Você pode conceder confiança total para a solução do Office ao assinar os manifestos de aplicativo e implantação.

 Os usuários finais podem conceder confiança à solução do Office, fazendo uma decisão de confiança no [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt confiável.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

##  <a name="Signing"></a> A solução de confiança ao assinar os manifestos de aplicativo e implantação
 Manifestos de todos os aplicativos e implantação do Office soluções devem ser assinadas com um certificado que identifica o Editor. Certificados fornecem uma base para tomar decisões de confiança.

 Um certificado temporário é criado para você e concedido confiança no momento da compilação para a solução seja executado enquanto você depurá-lo. Se você publicar uma solução que é assinada com um certificado temporário, o usuário final será solicitado a tomar uma decisão de confiança.

 Se você assinar a solução com um certificado conhecido e confiável, a solução será instalada automaticamente sem avisar o usuário final para tomar uma decisão de confiança. Para obter mais informações sobre como obter um certificado para assinar, consulte [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md). Depois de obter um certificado, o certificado deve ser explicitamente confiável ao ser adicionado à lista de editores confiáveis. Para obter mais informações, confira [Como: Adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

 Se um desenvolvedor fizer a solução com um certificado temporário, um administrador pode assinar novamente a personalização com um certificado conhecido e confiável usando o Manifest Generation and Editing Tool (*mage.exe*), que é uma da Ferramentas do Microsoft .NET Framework. Para obter mais informações sobre como assinar soluções, consulte [como: Assinar soluções do Office](../vsto/how-to-sign-office-solutions.md) e [como: Assinar manifestos de aplicativo e implantação](../ide/how-to-sign-application-and-deployment-manifests.md).

##  <a name="TrustPrompt"></a>A solução de confiança usando o prompt de confiança do ClickOnce
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] solicita que o usuário final para tomar a decisão de confiança, se não houver nenhuma política de toda a organização que relações de confiança de certificado da solução. Se o usuário final conceder confiança à solução, uma entrada de lista de inclusão é criada que contém uma URL e uma chave pública para armazenar essa decisão de confiança. Quando uma personalização confiável é executada mais tarde, o usuário final não é solicitado novamente.

 Os administradores podem desabilitar o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt confiável ou exigir que o prompt ocorrer apenas para as soluções que são assinadas com um certificado Authenticode. Para obter mais informações sobre como alterar essas configurações para as zonas de Meu computador, intranet local, Internet, TrustedSites e UntrustedSites, consulte [como: Configurar o comportamento do prompt confiável ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="see-also"></a>Consulte também

- [Proteger as soluções do Office](../vsto/securing-office-solutions.md)
- [Conceder confiança a documentos](../vsto/granting-trust-to-documents.md)
- [Solucionar problemas de segurança de solução do Office](../vsto/troubleshooting-office-solution-security.md)
- [Considerações sobre segurança específicas para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md)