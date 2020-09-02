---
title: Práticas recomendadas de segurança no VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697274"
---
# <a name="best-practices-for-security-in-vspackages"></a>Práticas de segurança recomendadas em VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para instalar o [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] em seu computador, você deve estar executando o em um contexto com credenciais administrativas. A unidade básica de segurança e implantação de um [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aplicativo é a [VSPackages](../../extensibility/internals/vspackages.md). Um VSPackage deve ser registrado usando o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , que também requer credenciais administrativas.  
  
 Os administradores têm permissões completas para gravar no registro e no sistema de arquivos e executar qualquer código. Você deve ter essas permissões para desenvolver, implantar ou instalar um VSPackage.  
  
 Assim que ele é instalado, um VSPackage é totalmente confiável. Devido a esse alto nível de permissão associado a um VSPackage, é possível instalar inadvertidamente um VSPackage que tenha uma intenção mal-intencionada.  
  
 Os usuários devem garantir que eles instalem o VSPackages somente de fontes confiáveis. As empresas que estão desenvolvendo o VSPackages devem nomear e assinar com segurança, para garantir ao usuário que a violação seja impedida. As empresas que estão desenvolvendo o VSPackages devem examinar suas dependências externas, como serviços Web e instalação remota, para avaliar e corrigir problemas de segurança.  
  
 Para obter mais informações, consulte Diretrizes de codificação segura para o .NET Framework ( [https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx) ).  
  
## <a name="see-also"></a>Consulte Também  
 [Segurança do suplemento](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [Segurança do DDEX](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
