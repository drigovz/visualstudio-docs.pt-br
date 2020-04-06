---
title: Assinatura de pacotes VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17179c35496fc19322c5bb951f4d04bc28e5d7bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700085"
---
# <a name="signing-vsix-packages"></a>Assinando pacotes VSIX
Os conjuntos de extensão não precisam ser assinados antes de serem executados no Visual Studio, mas é uma boa prática fazê-lo.

 Se você quiser proteger sua extensão e ter certeza de que ela não foi adulterada, você pode adicionar uma assinatura digital a um pacote VSIX. Quando um VSIX é assinado, o instalador VSIX exibirá uma mensagem indicando que está assinada, além de mais informações sobre a assinatura em si. Se o conteúdo do VSIX tiver sido modificado e o VSIX não tiver sido assinado novamente, o instalador VSIX mostrará que a assinatura não é válida. A instalação não está parada, mas o usuário é avisado.

> [!IMPORTANT]
> A partir do Visual Studio 2015, os pacotes VSIX assinados usando qualquer coisa que não seja a criptografia SHA256 serão identificados como tendo uma assinatura inválida. A instalação do VSIX não está bloqueada, mas o usuário será avisado.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Assinando um VSIX com o VSIXSignTool
 Há uma ferramenta de assinatura de criptografia SHA256 disponível no [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) em nuget.org no [VsixSignTool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Para usar o VSIXSignTool

1. Adicione seu VSIX a um projeto.

2. Clique com o botão direito do mouse no nó do projeto no Solution Explorer, selecionando **Adicionar &#124; Gerenciar pacotes NuGet**.  Para obter mais informações sobre o NuGet e adicionar pacotes NuGet, consulte os tópicos de [ida](/NuGet) e vida do NuGet e [do Gerenciador de](/NuGet/Tools/Package-Manager-UI) pacotes.

3. Procure o VSIXSignTool no VisualStudioExtensibility e instale o pacote NuGet.

4. Agora você pode executar o VSIXSignTool a partir da localização local dos pacotes do projeto. Consulte a ajuda da linha de comando da ferramenta para o seu cenário de assinatura (VSIXSignTool.exe /?).

   Por exemplo, para assinar com um arquivo de certificado protegido por senha:

   VSIXSignTool.exe sign \</f certfile \<> \</p senha> VSIXfile>

## <a name="see-also"></a>Confira também
- [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
