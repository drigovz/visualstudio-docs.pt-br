---
title: Melhores práticas de segurança em VSPackages | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709904"
---
# <a name="best-practices-for-security-in-vspackages"></a>Práticas recomendadas para segurança em VSPackages
Para instalar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] o em seu computador, você deve estar executando em um contexto com credenciais administrativas. A unidade básica de segurança [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e implantação de um aplicativo é o [VSPackage](../../extensibility/internals/vspackages.md). Um VSPackage deve ser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]registrado usando, o que também requer credenciais administrativas.

 Os administradores têm permissões completas para escrever no registro e no sistema de arquivos e executar qualquer código. Você deve ter essas permissões para desenvolver, implantar ou instalar um VSPackage.

 Assim que ele é instalado, um VSPackage é totalmente confiável. Devido a esse alto nível de permissão associado a um VSPackage, é possível instalar inadvertidamente um VSPackage que tenha intenção maliciosa.

 Os usuários devem garantir que eles instalem VSPackages apenas a partir de fontes confiáveis. As empresas que desenvolvem VSPackages devem nomeá-los e assiná-los fortemente, para garantir ao usuário que a adulteração seja evitada. As empresas que desenvolvem VSPackages devem examinar suas dependências externas, como serviços web e instalação remota, para avaliar e corrigir quaisquer problemas de segurança.

 Para obter mais informações, consulte [Diretrizes de codificação Segura para o Quadro .NET](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Confira também
- [Segurança de complemento](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Segurança DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
