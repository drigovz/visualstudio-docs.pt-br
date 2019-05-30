---
title: Assinar pacotes VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 710cc523cdd01ad431572860ace9b06af3cff418
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332089"
---
# <a name="signing-vsix-packages"></a>Assinando pacotes VSIX
Assemblies de extensão não é necessário ser assinados antes que eles podem executar no Visual Studio, mas é uma boa prática fazer isso.

 Se você quiser proteger sua extensão e verifique se que ele não foi adulterado, você pode adicionar uma assinatura digital a um pacote VSIX. Quando está conectado a um VSIX, o instalador do VSIX exibirá uma mensagem indicando que ele está assinado, além de obter mais informações sobre a assinatura em si. Se o conteúdo do VSIX foi modificado e VSIX não foi assinado novamente, o instalador do VSIX mostrará que a assinatura não é válida. A instalação não for interrompida, mas o usuário é avisado.

> [!IMPORTANT]
> Começando com o Visual Studio 2015, os pacotes VSIX assinados usando algo diferente de criptografia de SHA256 serão identificados como tendo uma assinatura inválida. Instalação de VSIX não é bloqueada, mas o usuário será avisado.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Assinar um VSIX com VSIXSignTool
 Há uma ferramenta disponível a partir de assinatura de criptografia de SHA256 [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) em nuget.org em [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Para usar o VSIXSignTool

1. Adicione seu VSIX a um projeto.

2. Clique com botão direito no nó do projeto no Gerenciador de soluções, selecionando **adicionar &#124; gerenciar pacotes NuGet**.  Para obter mais informações sobre a adição de NuGet e NuGet pacotes Consulte os [documentação do NuGet](/NuGet) e [Gerenciador de pacotes UI](/NuGet/Tools/Package-Manager-UI) tópicos.

3. Pesquisar VSIXSignTool de VisualStudioExtensibility e instalar o pacote do NuGet.

4. Agora você pode executar o VSIXSignTool de local de pacotes local do projeto. Consulte a Ajuda de linha de comando da ferramenta para seu cenário de autenticação (VSIXSignTool.exe /?).

   Por exemplo, para entrar com uma senha protegida no arquivo de certificado:

   VSIXSignTool.exe entrada /f \<certfile >/p \<senha > \<VSIXfile >

## <a name="see-also"></a>Consulte também
- [Enviar extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
