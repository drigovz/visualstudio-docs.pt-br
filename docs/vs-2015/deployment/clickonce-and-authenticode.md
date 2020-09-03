---
title: ClickOnce e Authenticode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8f7fd108250a406339d5be08b5a6e9aaf67d039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917559"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce e Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode * é uma tecnologia da Microsoft que usa a criptografia padrão da indústria para assinar o código do aplicativo com certificados digitais que verificam a autenticidade do editor do aplicativo. Ao usar o Authenticode para a implantação de aplicativos, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] o reduz o risco de um cavalo de Troia. Um cavalo de Troia é um vírus ou outro programa prejudicial que uma terceira parte mal-intencionada representa indefinidamente como um programa legítimo proveniente de uma fonte confiável e estabelecida. A assinatura de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantações com um certificado digital é uma etapa opcional para verificar se os assemblies e arquivos não foram violados.  
  
 As seções a seguir descrevem os diferentes tipos de certificados digitais usados em Authenticode, como os certificados são validados usando CAs (autoridades de certificação), a função de carimbo de data/hora em certificados e os métodos de armazenamento disponíveis para certificados.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode e assinatura de código  
 Um *certificado digital* é um arquivo que contém um par de chaves públicas/privadas de criptografia, junto com os metadados que descrevem o editor para o qual o certificado foi emitido e a agência que emitiu o certificado.  
  
 Há vários tipos de certificados Authenticode. Cada uma está configurada para diferentes tipos de assinatura. Para [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos, você deve ter um certificado Authenticode válido para assinatura de código. Se você tentar assinar um [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo com outro tipo de certificado, como um certificado de email digital, ele não funcionará. Para saber mais, confira [Introdução à Assinatura de Código](https://msdn.microsoft.com/library/ms537361.aspx).  
  
 Você pode obter um certificado para a assinatura de código de uma das três maneiras:  
  
- Compre um de um fornecedor de certificado.  
  
- Receba uma de um grupo em sua organização responsável pela criação de certificados digitais.  
  
- Gere seu próprio certificado com MakeCert.exe, que está incluído no [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] .  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Como usar autoridades de certificação ajuda os usuários  
 Um certificado gerado usando o utilitário MakeCert.exe é normalmente chamado de certificado de *autoatendimento* ou de *teste*. Esse tipo de certificado funciona muito da mesma maneira que um arquivo. SNK funciona no .NET Framework. Ele consiste apenas em um par de chaves criptográficas pública/privada e não contém informações verificáveis sobre o Publicador. Você pode usar certificados automáticos para implantar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos com alta confiança em uma intranet. No entanto, quando esses aplicativos são executados em um computador cliente, os [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] identificam como provenientes de um Publicador desconhecido. Por padrão, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] os aplicativos assinados com autocert e implantados pela Internet não podem utilizar a implantação de aplicativos confiáveis.  
  
 Por outro lado, se você receber um certificado de uma autoridade de certificação, como um fornecedor de certificado ou um departamento dentro de sua empresa, o certificado oferecerá mais segurança para seus usuários. Ele não apenas identifica o editor do software assinado, mas verifica essa identidade verificando a autoridade de certificação que a assinou. Se a autoridade de certificação não for a autoridade raiz, o Authenticode também "encadeará" à autoridade raiz para verificar se a autoridade de certificação está autorizada a emitir certificados. Para maior segurança, você deve usar um certificado emitido por uma autoridade de certificação sempre que possível.  
  
 Para obter mais informações sobre como gerar certificados automáticos, consulte [Makecert.exe (ferramenta de criação de certificado)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Carimbos de data/hora  
 Os certificados usados para assinar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos expiram após um determinado período de tempo, normalmente de doze meses. Para remover a necessidade de assinar constantemente os aplicativos com novos certificados, o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dá suporte a carimbo de data/hora. Quando um aplicativo é assinado com um carimbo de data/hora, seu certificado continuará a ser aceito mesmo após a expiração, desde que o carimbo de data/hora seja válido. Isso permite que [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativos com certificados expirados, mas carimbos de data/hora válidos, sejam baixados e executados. Ele também permite que aplicativos instalados com certificados expirados continuem a baixar e instalar atualizações.  
  
 Para incluir um carimbo de data/hora em um servidor de aplicativos, um servidor de carimbo de data/hora deve estar disponível. Para obter informações sobre como selecionar um servidor de carimbo de data/hora, consulte [como assinar manifestos de aplicativo e implantação](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Atualizando certificados expirados  
 Em versões anteriores do .NET Framework, a atualização de um aplicativo cujo certificado expirou poderia fazer com que esse aplicativo pare de funcionar. Para resolver esse problema, use um dos seguintes métodos:  
  
- Atualize o .NET Framework para a versão 2,0 SP1 ou posterior no Windows XP ou na versão 3,5 ou posterior no Windows Vista.  
  
- Desinstale o aplicativo e reinstale uma nova versão com um certificado válido.  
  
- Crie um assembly de linha de comando que atualize o certificado.  
  
### <a name="storing-certificates"></a>Armazenando certificados  
  
- Você pode armazenar certificados como um arquivo. pfx no sistema de arquivos ou pode armazená-los dentro de um contêiner de chave. Um usuário em um domínio do Windows pode ter um número de contêineres de chave. Por padrão, MakeCert.exe armazenará certificados em seu contêiner de chave pessoal, a menos que você especifique que ele deve salvá-lo em um. pfx em vez disso. Mage.exe e MageUI.exe, as [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] ferramentas para a criação de [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantações, permitem que você use certificados armazenados de qualquer maneira.  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
