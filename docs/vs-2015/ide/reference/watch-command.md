---
title: Comando de Inspeção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd362c01c996dc6a32197b9acd88f11b26c034bf
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655797"
---
# <a name="watch-command"></a>Comando Inspecionar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cria e abre uma instância especificada de uma janela **Inspeção**. Você pode usar uma janela **Inspeção** para calcular os valores de variáveis, expressões e registros, para editar esses valores e para salvar os resultados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Necessário. O número de instância da janela Inspeção.  
  
## <a name="remarks"></a>Comentários  
 O `index` deve ser um inteiro. Os valores válidos são 1, 2, 3 ou 4.  
  
## <a name="example"></a>Exemplo  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Consulte também  
 [Janelas automáticas e locais](../../debugger/autos-and-locals-windows.md)   
 [Como editar um valor em uma janela variável](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Como usar a caixa de diálogo QuickWatch](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
