---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657915"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Notifica o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para mesclar os pacotes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no sistema e verificar o cache MEF para as alterações.

## <a name="syntax"></a>Sintaxe

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Comentários
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] executa este comando automaticamente quando você instala um pacote VSIX. Você deve executar `devenv.exe /updateconfiguration` após a aplicação de patch em seus arquivos de modo que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] atualize o cache MEF. Isso permite que você avalie se a correção é adequada.

## <a name="example"></a>Exemplo
 A linha de comando a seguir faz com que [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mescle os pacotes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no sistema e verifique o cache MEF para quaisquer eventuais alterações.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Consulte Também
 [Personalizando as configurações de desenvolvimento nas opções de linha de comando do devenv do Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)
