---
title: Adicionar verificações de nulo para todos (os parâmetros)
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74782303"
---
# <a name="add-null-checks-for-all-parameters"></a>Adicionar verificações de nulo para todos os parâmetros 

Esta refatoração aplica-se a: 

- C# 

**O que:** Cria e adiciona instruções `if` que verificam a nulidade de todos os parâmetros anuláveis e não verificados. 

**Quando:** Você deseja adicionar rapidamente verificações nulas para todos os parâmetros de método aplicáveis.

**Por que:** Escrever verificações nulas para muitos parâmetros pode ser demorado e repetitivo. O uso dessa refatoração é rápido e torna o programa mais robusto.  

## <a name="how-to"></a>Como fazer 

1. Coloque o cursor em qualquer parâmetro dentro do método.

2. Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Ações e refatorações rápidas](media/add-null-checks-for-all-parameters.png)
   
3. Selecione a opção para **Adicionar verificações de nulo para todos os parâmetros**.

   ![Adicionar verificações de nulo para todos](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Consulte também 

- [Refatoração](../refactoring-in-visual-studio.md)
