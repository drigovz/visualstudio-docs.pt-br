---
title: Práticas recomendadas para segurança em VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 308832522b4badde661d4132410ca8366856d7b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910510"
---
# <a name="best-practices-for-security-in-vspackages"></a>Práticas recomendadas de segurança em VSPackages
Para instalar o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] no seu computador, você deve estar executando em um contexto com credenciais administrativas. A unidade básica de segurança e a implantação de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicativo é o [VSPackage](../../extensibility/internals/vspackages.md). Um VSPackage deverá ser registrado usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que também requer credenciais administrativas.

 Os administradores têm permissões completas para escrever no registro e sistema de arquivos e executar qualquer código. Você deve ter essas permissões para desenvolver, implantar ou instalar um VSPackage.

 Assim que ele é instalado, um VSPackage é totalmente confiável. Devido a esse nível alto de permissão associada a um VSPackage, é possível instalar inadvertidamente um VSPackage que tenha más intenções.

 Os usuários devem garantir que eles instalar VSPackages somente de fontes confiáveis. As empresas desenvolvendo os VSPackages fortemente devem nomear e assiná-las garantir que o usuário dessa violação é impedido. As empresas desenvolvendo os VSPackages devem examinar suas dependências externas, como serviços da web e de instalação remota, para avaliar e corrigir quaisquer problemas de segurança.

 Para obter mais informações, consulte [segura de diretrizes de codificação para o .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Consulte também
- [Segurança de suplemento](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Segurança DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)