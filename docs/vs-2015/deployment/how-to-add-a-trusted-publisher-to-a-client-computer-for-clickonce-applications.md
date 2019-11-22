---
title: 'Como: adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b535737860b846aadecb6b73b4bd26659db37b1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74289714"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Como adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com a implantação de aplicativo confiável, você pode configurar computadores cliente para que seus aplicativos de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] sejam executados com um nível mais alto de confiança sem avisar o usuário. Os procedimentos a seguir mostram como usar a ferramenta de linha de comando CertMgr. exe para adicionar o certificado de um editor ao repositório de editores confiáveis em um computador cliente.  
  
 Os comandos usados variam um pouco dependendo se a AC (autoridade de certificação) que emitiu o certificado faz parte da raiz confiável de um cliente. Se um computador cliente do Windows fizer parte de um domínio, ele conterá, em uma lista, CAs que são consideradas raízes confiáveis. Essa lista geralmente é configurada pelo administrador do sistema. Se o certificado foi emitido por uma dessas raízes confiáveis ou por uma autoridade de certificação que se encadeia a uma dessas raízes confiáveis, você pode adicionar o certificado ao armazenamento raiz confiável do cliente. Se, por outro lado, o certificado não tiver sido emitido por uma dessas raízes confiáveis, você deverá adicionar o certificado ao repositório de raiz confiável do cliente e ao repositório de publicador confiável.  
  
> [!NOTE]
> Você deve adicionar certificados dessa maneira em cada computador cliente ao qual planeja implantar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo que requer permissões elevadas. Você adiciona os certificados manualmente ou por meio de um aplicativo implantado em seus clientes. Você só precisa configurar esses computadores uma vez, após o qual é possível implantar qualquer número de aplicativos [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] assinados com o mesmo certificado.  
  
 Você também pode adicionar um certificado a um armazenamento programaticamente usando a classe <xref:System.Security.Cryptography.X509Certificates.X509Store>.  
  
 Para obter uma visão geral da implantação de aplicativos confiáveis, consulte [visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Para adicionar um certificado ao repositório de editores confiáveis na raiz confiável  
  
1. Obtenha um certificado digital de uma autoridade de certificação.  
  
2. Exporte o certificado para o formato base64 X. 509 (. cer). Para obter mais informações sobre formatos de certificado, consulte [exportar um certificado](https://go.microsoft.com/fwlink/?LinkId=164793).  
  
3. No prompt de comando em computadores cliente, execute o seguinte comando:  
  
     **Certmgr. exe-adicionar certificado. cer-c-s-r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Para adicionar um certificado ao repositório de editores confiáveis em uma raiz diferente  
  
1. Obtenha um certificado digital de uma autoridade de certificação.  
  
2. Exporte o certificado para o formato base64 X. 509 (. cer). Para obter mais informações sobre formatos de certificado, consulte [exportar um certificado](https://go.microsoft.com/fwlink/?LinkId=164793).  
  
3. No prompt de comando em computadores cliente, execute o seguinte comando:  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **Certmgr. exe-adicione Good. cer-c-s-r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Consulte também  
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)  (Instruções passo a passo: implantando manualmente um aplicativo ClickOnce)  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Como habilitar configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Como definir uma zona de segurança para um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Como depurar um aplicativo ClickOnce com permissões restritas](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Como: adicionar um fornecedor confiável a um computador cliente para aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Como: assinar novamente manifestos de aplicativo e implantação](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Como configurar o comportamento do prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
