---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac542ded884e922028c6cbc16447fb2a3241613b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663278"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre o arquivo executável especificado a ser depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Arguments  
 `ExecutableFile`  
 Necessário. O caminho e o nome de um arquivo .exe.  
  
 Se o arquivo .exe não for encontrado ou não existir, nenhum aviso nem erro será exibido, e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] iniciará normalmente.  
  
## <a name="remarks"></a>Comentários  
 Quaisquer cadeias de caracteres após o parâmetro `ExecutableFile` são passadas para esse arquivo como argumentos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir abre o arquivo `MyApplication.exe` para depuração.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
