---
title: Assinando pacotes VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b74222804e9ed42e6f8263cbe6ad0daf19cda81f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300323"
---
# <a name="signing-vsix-packages"></a>Assinando pacotes VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os assemblies de extensão não precisam ser assinados antes que possam ser executados no Visual Studio, mas é uma boa prática fazer isso.  
  
 Se você quiser proteger sua extensão e verificar se ela não foi violada, você pode adicionar uma assinatura digital a um pacote VSIX. Quando um VSIX é assinado, o instalador do VSIX exibirá uma mensagem indicando que ela está assinada, além de mais informações sobre a própria assinatura. Se o conteúdo do VSIX tiver sido modificado e o VSIX não tiver sido assinado novamente, o instalador do VSIX mostrará que a assinatura não é válida. A instalação não é interrompida, mas o usuário é avisado.  
  
> [!IMPORTANT]
> A partir do 2015, os pacotes VSIX assinados usando algo diferente da criptografia SHA256 serão identificados como tendo uma assinatura inválida. A instalação do VSIX não está bloqueada, mas o usuário será avisado.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Assinando um VSIX com o VSIXSignTool  
 Há uma ferramenta de assinatura de criptografia SHA256 disponível em [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) em NuGet.org em [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Para usar o VSIXSignTool  
  
1. Adicione seu VSIX a um projeto.  
  
2. Clique com o botão direito do mouse no nó do projeto em Gerenciador de Soluções, selecione **Adicionar &#124; gerenciar pacotes NuGet**.  Para obter mais informações sobre o NuGet e adicionar pacotes NuGet, consulte [visão geral do NuGet](https://docs.microsoft.com/nuget/) e [gerenciar pacotes NuGet usando a caixa de diálogo](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).  
  
3. Procure VSIXSignTool de VisualStudioExtensibility e instale o pacote NuGet.  
  
4. Agora você pode executar o VSIXSignTool no local de pacotes locais do projeto. Consulte a ajuda de linha de comando da ferramenta para seu cenário de assinatura (VSIXSignTool. exe/?).  
  
   Por exemplo, para assinar um arquivo de certificado protegido por senha:  
  
   VSIXSignTool. exe sinal/f \<CertFile >/p \<senha > \<VSIXfile >  
  
## <a name="see-also"></a>Consulte também  
 [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
