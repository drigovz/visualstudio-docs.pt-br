---
title: Práticas recomendadas de segurança no VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709904"
---
# <a name="best-practices-for-security-in-vspackages"></a>Práticas recomendadas de segurança no VSPackages
Para instalar o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] em seu computador, você deve estar executando o em um contexto com credenciais administrativas. A unidade básica de segurança e implantação de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicativo é a [VSPackage](../../extensibility/internals/vspackages.md). Um VSPackage deve ser registrado usando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , que também requer credenciais administrativas.

 Os administradores têm permissões completas para gravar no registro e no sistema de arquivos e executar qualquer código. Você deve ter essas permissões para desenvolver, implantar ou instalar um VSPackage.

 Assim que ele é instalado, um VSPackage é totalmente confiável. Devido a esse alto nível de permissão associado a um VSPackage, é possível instalar inadvertidamente um VSPackage que tenha uma intenção mal-intencionada.

 Os usuários devem garantir que eles instalem o VSPackages somente de fontes confiáveis. As empresas que estão desenvolvendo o VSPackages devem nomear e assinar com segurança, para garantir ao usuário que a violação seja impedida. As empresas que estão desenvolvendo o VSPackages devem examinar suas dependências externas, como serviços Web e instalação remota, para avaliar e corrigir problemas de segurança.

 Para obter mais informações, consulte [diretrizes de codificação segura para o .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Confira também
- [Segurança do suplemento](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Segurança do DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
