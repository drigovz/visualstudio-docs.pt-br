---
title: ClickOnce e Authenticode | Microsoft Docs
description: Saiba mais sobre os certificados que o Authenticode usa para verificar a autenticidade dos aplicativos. Saiba como os certificados são validados e armazenados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07b40cb9c4e1d79390bb4a0541e1cb5bd8862d3a
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383138"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce e Authenticode
O *Authenticode* é uma tecnologia da Microsoft que usa a criptografia padrão da indústria para assinar o código do aplicativo com certificados digitais que verificam a autenticidade do editor do aplicativo. Ao usar o Authenticode para a implantação de aplicativos, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o reduz o risco de um cavalo de Troia. Um cavalo de Troia é um vírus ou outro programa prejudicial que uma terceira parte mal-intencionada representa indefinidamente como um programa legítimo proveniente de uma fonte confiável e estabelecida. A assinatura de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações com um certificado digital é uma etapa opcional para verificar se os assemblies e arquivos não foram violados.

 As seções a seguir descrevem os diferentes tipos de certificados digitais usados em Authenticode, como os certificados são validados usando CAs (autoridades de certificação), a função de carimbo de data/hora em certificados e os métodos de armazenamento disponíveis para certificados.

## <a name="authenticode-and-code-signing"></a>Authenticode e assinatura de código
 Um *certificado digital* é um arquivo que contém um par de chaves públicas/privadas de criptografia, junto com os metadados que descrevem o editor para o qual o certificado foi emitido e a agência que emitiu o certificado.

 Há vários tipos de certificados Authenticode. Cada uma está configurada para diferentes tipos de assinatura. Para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos, você deve ter um certificado Authenticode válido para assinatura de código. Se você tentar assinar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo com outro tipo de certificado, como um certificado de email digital, ele não funcionará. Para obter mais informações, consulte [introdução à assinatura de código](/windows/desktop/seccrypto/cryptography-tools).

 Você pode obter um certificado para a assinatura de código de uma das três maneiras:

- Compre um de um fornecedor de certificado.

- Receba uma de um grupo em sua organização responsável pela criação de certificados digitais.

- Gere seu próprio certificado usando o cmdlet New-SelfSignedCertificate PowerShell ou usando *MakeCert.exe* , que está incluído no [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] .

### <a name="how-using-certificate-authorities-helps-users"></a>Como usar autoridades de certificação ajuda os usuários
 Um certificado gerado usando New-SelfSignedCertificate ou o utilitário *MakeCert.exe* é normalmente chamado de certificado de *autoatendimento* ou de *teste*. Esse tipo de certificado funciona muito da mesma maneira que um arquivo *. SNK* funciona no .NET Framework. Ele consiste apenas em um par de chaves criptográficas pública/privada e não contém informações verificáveis sobre o Publicador. Você pode usar certificados automáticos para implantar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos com alta confiança em uma intranet. No entanto, quando esses aplicativos são executados em um computador cliente, os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identificam como provenientes de um Publicador desconhecido. Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] os aplicativos assinados com autocert e implantados pela Internet não podem utilizar a implantação de aplicativos confiáveis.

 Por outro lado, se você receber um certificado de uma autoridade de certificação, como um fornecedor de certificado ou um departamento dentro de sua empresa, o certificado oferecerá mais segurança para seus usuários. Ele não apenas identifica o editor do software assinado, mas verifica essa identidade verificando a autoridade de certificação que a assinou. Se a autoridade de certificação não for a autoridade raiz, o Authenticode também "encadeará" à autoridade raiz para verificar se a autoridade de certificação está autorizada a emitir certificados. Para maior segurança, você deve usar um certificado emitido por uma autoridade de certificação sempre que possível.

 Para obter mais informações sobre como gerar certificados automáticos, consulte [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) ou [MakeCert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Carimbos de data/hora
 Os certificados usados para assinar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos expiram após um determinado período de tempo, normalmente de doze meses. Para remover a necessidade de assinar constantemente os aplicativos com novos certificados, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dá suporte a carimbo de data/hora. Quando um aplicativo é assinado com um carimbo de data/hora, seu certificado continuará a ser aceito mesmo após a expiração, desde que o carimbo de data/hora seja válido. Isso permite que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos com certificados expirados, mas carimbos de data/hora válidos, sejam baixados e executados. Ele também permite que aplicativos instalados com certificados expirados continuem a baixar e instalar atualizações.

 Para incluir um carimbo de data/hora em um servidor de aplicativos, um servidor de carimbo de data/hora deve estar disponível. Para obter informações sobre como selecionar um servidor de carimbo de data/hora, consulte [como assinar manifestos de aplicativo e implantação](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Atualizar certificados expirados
 Em versões anteriores do .NET Framework, a atualização de um aplicativo cujo certificado expirou poderia fazer com que esse aplicativo pare de funcionar. Para resolver esse problema, use um dos seguintes métodos:

- Atualize o .NET Framework para a versão 2,0 SP1 ou posterior no Windows XP ou na versão 3,5 ou posterior no Windows Vista.

- Desinstale o aplicativo e reinstale uma nova versão com um certificado válido.

### <a name="store-certificates"></a>Armazenar certificados

- Você pode armazenar certificados como um arquivo *. pfx* no sistema de arquivos ou pode armazená-los dentro de um contêiner de chave. Um usuário em um domínio do Windows pode ter um número de contêineres de chave. Por padrão, *MakeCert.exe* armazenará certificados em seu contêiner de chave pessoal, a menos que você especifique que ele deve salvá-lo em um *. pfx* em vez disso. *Mage.exe* e *MageUI.exe* , as [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] ferramentas para a criação de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações, permitem que você use certificados armazenados de qualquer maneira.

## <a name="see-also"></a>Confira também
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)