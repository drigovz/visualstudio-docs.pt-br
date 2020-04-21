---
title: Adicionar editor confiável ao computador cliente para aplicativos ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1423952405a31063ee88ce6fa1dfe0b75d80fe5d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649210"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Como adicionar um fornecedor confiável a um computador cliente em aplicativos ClickOnce
Com a implantação de aplicativos confiáveis, você [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pode configurar computadores clientes para que seus aplicativos seja executado com um nível mais alto de confiança sem solicitar ao usuário. Os procedimentos a seguir mostram como usar a ferramenta de linha de comando CertMgr.exe para adicionar um certificado de editor à loja Trusted Publishers em um computador cliente.

 Os comandos que você usa variam ligeiramente dependendo se a autoridade de certificado (CA) que emitiu seu certificado faz parte da raiz confiável de um cliente. Se um computador cliente Windows fizer parte de um domínio, ele conterá, em uma lista, CAs que são considerados raízes confiáveis. Esta lista geralmente é configurada pelo administrador do sistema. Se o seu certificado foi emitido por uma dessas raízes confiáveis, ou por uma CA que se acorrenta a uma dessas raízes confiáveis, você pode adicionar o certificado ao armazenamento raiz confiável do cliente. Se, por outro lado, seu certificado não foi emitido por uma dessas raízes confiáveis, você deve adicionar o certificado tanto à loja Trusted Root do cliente quanto à loja Trusted Publisher.

> [!NOTE]
> Você deve adicionar certificados desta forma em cada computador [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cliente ao qual você planeja implantar um aplicativo que exija permissões elevadas. Você adiciona os certificados manualmente ou através de um aplicativo que você implanta para seus clientes. Você só precisa configurar esses computadores uma vez, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] depois do qual você pode implantar qualquer número de aplicativos assinados com o mesmo certificado.

 Você também pode adicionar um certificado a <xref:System.Security.Cryptography.X509Certificates.X509Store> uma loja programáticamente usando a classe.

 Para obter uma visão geral da implantação de aplicativos confiáveis, consulte [visão geral de implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md).

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Para adicionar um certificado à loja Trusted Publishers sob a raiz confiável

1. Obtenha um certificado digital de um CA.

2. Exporte o certificado para o formato Base64 X.509 (*.cer).* Para obter mais informações sobre formatos de certificado, consulte [Exportar um certificado](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. A partir do prompt de comando nos computadores clientes, execute o seguinte comando:

     **certmgr.exe -add certificate.cer -c-s -r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Para adicionar um certificado à loja Trusted Publishers sob uma raiz diferente

1. Obtenha um certificado digital de um CA.

2. Exporte o certificado para o formato Base64 X.509 (*.cer).* Para obter mais informações sobre formatos de certificado, consulte [Exportar um Certificado](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. A partir do prompt de comando nos computadores clientes, execute o seguinte comando:

     **certmgr.exe -add good.cer -c -s -r localMachine Root**

     **certmgr.exe -add good.cer -c-s -r localMachine TrustedPublisher**

## <a name="see-also"></a>Confira também
- [Passo a passo: Implantar um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)
- [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)
- [Como habilitar as configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Como definir uma zona de segurança em um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Como definir permissões personalizadas em um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Como depurar um aplicativo ClickOnce com permissões restritas](securing-clickonce-applications.md)
- [Como adicionar um fornecedor confiável a um computador cliente em aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Como reassinar manifestos do aplicativo e de implantação](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Como configurar o comportamento do prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)