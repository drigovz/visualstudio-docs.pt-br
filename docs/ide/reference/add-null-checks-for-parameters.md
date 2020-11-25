---
title: Adicionar verificações de nulo para todos (os parâmetros)
description: Saiba como criar e adicionar instruções if ao seu código que verificam a nulidade de todos os parâmetros anuláveis e não verificados.
ms.custom: SEO-VS-2020
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5828a2bb28f7b3085cd5d43c452c520a730b8175
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870957"
---
# <a name="add-null-checks-for-all-parameters"></a>Adicionar verificações de nulo para todos os parâmetros 

Esta refatoração aplica-se a: 

- C# 

**O que:** Cria e adiciona `if` instruções que verificam a nulidade de todos os parâmetros anuláveis e não verificados. 

**Quando:** Você deseja adicionar rapidamente verificações nulas para todos os parâmetros de método aplicáveis.

**Por que:** Escrever verificações nulas para muitos parâmetros pode ser demorado e repetitivo. O uso dessa refatoração é rápido e torna o programa mais robusto.  

## <a name="how-to"></a>Como fazer 

1. Coloque o cursor em qualquer parâmetro dentro do método.

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Ações e refatorações rápidas](media/add-null-checks-for-all-parameters.png)
   
3. Selecione a opção para **adicionar verificações nulas para todos os parâmetros**.

   ![Adicionar verificações de nulo para todos](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Confira também 

- [Refatoração](../refactoring-in-visual-studio.md)
