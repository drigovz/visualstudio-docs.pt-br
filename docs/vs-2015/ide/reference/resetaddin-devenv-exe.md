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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9958e6e9a540dce1a405df8991780600b8f4a702
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665597"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Remove comandos e comando da interface do usuário associado ao Suplemento especificado.

## <a name="syntax"></a>Sintaxe

```
Devenv /ResetAddin AddIn
```

## <a name="arguments"></a>Argumentos
 `AddIn` Opcional. O nome de comando do Suplemento.

## <a name="remarks"></a>Comentários
 Por padrão, o nome do comando do suplemento é igual a *\<AddInSolutionName>* . Conecte-se<em>. \<AddInSolutionName> </em>e aparece em Connect.cs como o `commandName` parâmetro do `Exec` método. Você também pode verificar o nome do comando começando a digitar o nome do suplemento na janela Comandos no Visual Studio e usando o IntelliSense para preencher o restante.

## <a name="example"></a>Exemplo
 O exemplo a seguir inicia o Visual Studio e impede o suplemento `MyAddin` de ser executado na inicialização.

```
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin
```

## <a name="see-also"></a>Consulte Também
 [Personalizando as configurações de desenvolvimento nas opções de linha de comando do devenv do Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)
