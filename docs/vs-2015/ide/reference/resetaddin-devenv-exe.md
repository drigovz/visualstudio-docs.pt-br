---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 241d97dd7b2b939ff49656e2cef2c93e4cb9b57b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656027"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Remove comandos e comando da interface do usuário associado ao Suplemento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Arguments  
 `AddIn`  
 Opcional. O nome de comando do Suplemento.  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o nome do comando do suplemento é igual a *\<AddInSolutionName>*.Connect<em>.\<AddInSolutionName></em> e aparece no Connect.cs como o parâmetro `commandName` do método `Exec`. Você também pode verificar o nome do comando começando a digitar o nome do suplemento na janela Comandos no Visual Studio e usando o IntelliSense para preencher o restante.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inicia o Visual Studio e impede o suplemento `MyAddin` de ser executado na inicialização.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
