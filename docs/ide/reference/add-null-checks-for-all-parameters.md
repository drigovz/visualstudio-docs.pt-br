---
title: Adicionar verificações de nulo para todos (os parâmetros)
ms.date: 07/24/2019
ms.topic: reference
author: stcahlon
ms.author: t-shzach
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: da3a616844dbe914cfe796ec35d1501bf83dd1ef
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712728"
---
# <a name="add-null-checks-for-all-parameters"></a>Adicionar verificações de nulo para todos os parâmetros 

Esta refatoração aplica-se a: 

- C# 

**O quê:** cria e adiciona instruções `if` que verificam a nulidade de todos os parâmetros anuláveis não verificados. 

**Quando:** você quer adicionar rapidamente verificações de nulo em todos os parâmetros de método aplicáveis.

**Por que:** gravar verificações de nulo para muitos parâmetros pode ser demorado e repetitivo. O uso dessa refatoração é rápido e torna o programa mais robusto.  

## <a name="how-to"></a>Como fazer 

1. Coloque o cursor em qualquer parâmetro dentro do método.

2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Ações e refatorações rápidas](media/add-null-checks-for-all-parameters.png)
   
3. Selecione a opção para **Adicionar verificações de nulo para todos os parâmetros**.

   ![Adicionar verificações de nulo para todos](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Consulte também 

- [Refatoração](../refactoring-in-visual-studio.md) 
