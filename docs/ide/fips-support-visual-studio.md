---
title: Suporte visual studio para o modo de operação aprovado FIPS 140-2
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06d147397a168bb78a31a8fbe6929d6c2184d080
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81386445"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Suporte visual studio para o modo de operação aprovado FIPS 140-2

A partir da [versão 16.4](/visualstudio/releases/2019/release-notes-v16.4/), o Visual Studio 2019 suporta o modo de operação aprovado pelo Federal Information Processing Standard (FIPS) Publicação 140-2 aprovada para Windows, Azure e .NET. E, com [a versão 16.5,](/visualstudio/releases/2019/release-notes-v16.5/)o Visual Studio agora suporta o modo de operação aprovado pelo FIPS 140-2 quando você desenvolve [aplicativos C++ que visam um sistema Linux remoto.](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)

Para configurar o modo de operação aprovado pelo FIPS 140-2 para o Visual Studio, instale o [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) e, em seguida, habilite a configuração de Diretiva de Grupo, **criptografia do sistema: Use algoritmos compatíveis com FIPS para criptografia, hashing e assinatura**.

Para obter mais informações sobre o modo de operação aprovado pelo FIPS 140-2 e como habilitá-lo, consulte [validação FIPS 140-2](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> As ferramentas que você usa para desenvolver aplicativos para plataformas não-Microsoft como iOS ou Android podem não usar algoritmos compatíveis com FIPS. Software de terceiros incluído no Visual Studio ou extensões que você instala também pode não usar algoritmos compatíveis com FIPS. E o desenvolvimento das soluções [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) não suporta o modo de operação aprovado pelo FIPS 140-2.

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre o modo de operação aprovado pelo FIPS 140-2 para o Visual Studio e para outros produtos e serviços da Microsoft, consulte os seguintes links:

- [Visual Studio: Configure o desenvolvimento seguro de Linux remoto compatível com FIPS com C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: Criptografia do sistema e o uso de algoritmos compatíveis com FIPS para criptografia, hashing e assinatura](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: conformidade fips](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Confira também

[Aplicativos seguros](securing-applications.md)