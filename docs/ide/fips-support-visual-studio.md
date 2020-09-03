---
title: Suporte do Visual Studio para o modo de operação aprovado pelo FIPS 140-2
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d06204fd1ef6ee2deb5eadc514af1ede8ae9bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84180487"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Suporte do Visual Studio para o modo de operação aprovado pelo FIPS 140-2

A partir da [versão 16,4](/visualstudio/releases/2019/release-notes-v16.4/), o Visual Studio 2019 dá suporte à publicação do padrão FIPS (FIPS) 140-2 modo de operação aprovado para Windows, Azure e .net. E, com a [versão 16,5](/visualstudio/releases/2019/release-notes-archive-v16.5), o Visual Studio agora dá suporte ao modo de operação aprovado pelo FIPS 140-2 quando você desenvolve [aplicativos C++ destinados a um sistema Linux remoto](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

Para configurar o modo de operação aprovado pelo FIPS 140-2 para o Visual Studio, [instale .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) e, em seguida, habilite a configuração política de grupo, **criptografia do sistema: usar algoritmos compatíveis com FIPS para criptografia, hash e assinatura**.

Para obter mais informações sobre o modo de operação aprovado pelo FIPS 140-2 e como habilitá-lo, consulte [validação do fips 140-2](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> As ferramentas que você usa para desenvolver aplicativos para plataformas que não sejam da Microsoft, como iOS ou Android, podem não usar algoritmos compatíveis com FIPS. Softwares de terceiros incluídos no Visual Studio ou extensões que você instalar também podem não usar algoritmos compatíveis com FIPS. E, o desenvolvimento para soluções [do SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) não dá suporte ao modo de operação aprovado pelo FIPS 140-2.

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre o modo de operação aprovado pelo FIPS 140-2 para o Visual Studio e para outros produtos e serviços da Microsoft, consulte os links a seguir:

- [Visual Studio: configurar o desenvolvimento Linux remoto seguro em conformidade com FIPS com o C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: criptografia do sistema e uso de algoritmos compatíveis com FIPS para criptografia, hash e assinatura](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core: conformidade com FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>Confira também

[Aplicativos seguros](securing-applications.md)
