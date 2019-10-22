---
title: Comando Inspeção Rápida | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da9ba9572e121a9eba74cd8d624789032f1bb4a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665663"
---
# <a name="quick-watch-command"></a>Comando Inspeção Rápida
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Exibe o texto selecionado ou especificado no campo Expressão da [Caixa de diálogo QuickWatch](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). Você pode usar essa caixa de diálogo para calcular o valor atual de uma variável ou expressão reconhecida pelo depurador ou o conteúdo de um registro. Além disso, você pode alterar o valor de qualquer variável não const ou o conteúdo de qualquer registro.

## <a name="syntax"></a>Sintaxe

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Arguments
 `text` Opcional. O texto a ser adicionado à caixa de diálogo **Inspeção Rápida**.

## <a name="remarks"></a>Comentários
 Se `text` for omitido, o texto selecionado atualmente ou a palavra no cursor é adicionada à janela Inspeção.

## <a name="example"></a>Exemplo

```
>Debug.QuickWatch
```

## <a name="see-also"></a>Veja também
 [Como: usar a caixa de diálogo QuickWatch da janela de comando de](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [comandos do Visual Studio](../../ide/reference/visual-studio-commands.md) [](../../ide/reference/command-window.md) comando [Localizar/](../../ide/find-command-box.md) usar a caixa de comando aliases de [comandos do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
