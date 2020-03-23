---
title: ClickOnce e Authenticode | Microsoft Docs
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
ms.openlocfilehash: b9b0e22f56ab68be521eda7a765a2be7e23bbf92
ms.sourcegitcommit: 6c3aa85ff17916936018d121e7a0d1b486f6c7eb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093956"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce e Authenticode
*Authenticode* é uma tecnologia da Microsoft que usa criptografia padrão do setor para assinar código de aplicativo com certificados digitais que verificam a autenticidade do editor do aplicativo. Ao usar o Authenticode [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para implantação de aplicativos, reduz o risco de um cavalo de Tróia. Um cavalo de Tróia é um vírus ou outro programa prejudicial que um terceiro mal-intencionado deturpa como um programa legítimo vindo de uma fonte estabelecida e confiável. Assinar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantações com um certificado digital é uma etapa opcional para verificar se os conjuntos e arquivos não são adulterados.

 As seções a seguir descrevem os diferentes tipos de certificados digitais usados no Authenticode, como os certificados são validados usando CAs (Certificate Authorities), o papel do carimbo de tempo nos certificados e os métodos de armazenamento disponíveis para Certificados.

## <a name="authenticode-and-code-signing"></a>Autenticação e assinatura de código
 Um *certificado digital* é um arquivo que contém um par de chaves criptográficas públicas/privadas, juntamente com metadados descrevendo o editor para quem o certificado foi emitido e a agência que emitiu o certificado.

 Existem vários tipos de certificados Authenticode. Cada uma é configurada para diferentes tipos de assinatura. Para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicações, você deve ter um certificado Authenticode válido para assinatura de código. Se você tentar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] assinar um aplicativo com outro tipo de certificado, como um certificado de e-mail digital, ele não funcionará. Para obter mais informações, consulte [Introdução à assinatura de código](/windows/desktop/seccrypto/cryptography-tools).

 Você pode obter um certificado para assinatura de código de uma das três maneiras:

- Compre um de um fornecedor de certificados.

- Receba um de um grupo em sua organização responsável pela criação de certificados digitais.

- Gere seu próprio certificado usando o cmdlet PowerShell do New-SelfSignedCertificate ou usando o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] *MakeCert.exe*, que está incluído no .

### <a name="how-using-certificate-authorities-helps-users"></a>Como o uso de autoridades de certificadoajuda os usuários
 Um certificado gerado usando o New-SelfSignedCertificate ou o utilitário *MakeCert.exe* é comumente chamado *de self-cert* ou um *certificado de teste*. Esse tipo de certificado funciona da mesma forma que um arquivo *.snk* funciona no .NET Framework. Ele consiste exclusivamente de um par de chaves criptográficas públicas/privadas, e não contém informações verificáveis sobre o editor. Você pode usar auto-certs para implantar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos com alta confiança em uma intranet. No entanto, quando esses aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] são executados em um computador cliente, os identificará como provenientes de um Editor Desconhecido. Por padrão, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] os aplicativos assinados com auto-certs e implantados na Internet não podem utilizar a implantação de aplicativos confiáveis.

 Em contrapartida, se você receber um certificado de um CA, como um fornecedor de certificados ou um departamento dentro de sua empresa, o certificado oferece mais segurança para seus usuários. Ele não só identifica o editor do software assinado, mas verifica essa identidade verificando com o CA que o assinou. Se a CA não for a autoridade raiz, a Authenticode também "acorrentará" a autoridade raiz para verificar se a CA está autorizada a emitir certificados. Para maior segurança, você deve usar um certificado emitido por um CA sempre que possível.

 Para obter mais informações sobre a geração de auto-certs, consulte [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) ou [MakeCert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Carimbos de data/hora
 Os certificados usados para assinar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pedidos expiram após um certo período de tempo, normalmente doze meses. Para remover a necessidade de reassinar constantemente os aplicativos [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] com novos certificados, suporta carimbo de data e hora. Quando um pedido é assinado com um carimbo de data e hora, seu certificado continuará a ser aceito mesmo após o vencimento, desde que o carimbo de data e hora seja válido. Isso [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] permite que aplicativos com certificados vencidos, mas carimbos válidos, baixem e executem. Também permite que aplicativos instalados com certificados expirados continuem a baixar e instalar atualizações.

 Para incluir um carimbo de tempo em um servidor de aplicativo, um servidor de carimbo de tempo deve estar disponível. Para obter informações sobre como selecionar um servidor de carimbo de tempo, consulte [Como: Assinar manifestos de aplicação e implantação](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Atualizar certificados vencidos
 Em versões anteriores do .NET Framework, atualizar um aplicativo cujo certificado expirou poderia fazer com que esse aplicativo parasse de funcionar. Para resolver esse problema, use um dos seguintes métodos:

- Atualize o .NET Framework para a versão 2.0 SP1 ou posterior no Windows XP, ou a versão 3.5 ou posterior no Windows Vista.

- Desinstale o aplicativo e reinstale uma nova versão com um certificado válido.

### <a name="store-certificates"></a>Armazenar certificados

- Você pode armazenar certificados como um arquivo *.pfx* em seu sistema de arquivos, ou você pode armazená-los dentro de um contêiner de chaves. Um usuário em um domínio do Windows pode ter uma série de contêineres-chave. Por padrão, *o MakeCert.exe* armazenará certificados em seu contêiner de chaves pessoais, a menos que você especifique que ele deve salvá-lo em um *.pfx* em vez disso. *Mage.exe* e *MageUI.exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] as ferramentas para criar implantações, permitem que você use certificados armazenados de qualquer forma.

## <a name="see-also"></a>Confira também
- [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
