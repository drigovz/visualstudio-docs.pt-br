---
title: Adicionar conversão explícita
ms.date: 03/26/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e159082266b848ce4742e436c706f3f71b2cc9ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84182970"
---
# <a name="add-explicit-cast"></a>Adicionar conversão explícita

Esta geração de código aplica-se a:

- C#

**O que:** Permite adicionar automaticamente uma conversão explícita a uma expressão, com base no uso.

**Quando:** Você precisa adicionar uma conversão explícita a uma expressão e desejar atribuí-la corretamente automaticamente.

**Por que:** Você pode adicionar uma conversão explícita a uma expressão manualmente; no entanto, esse recurso a adiciona automaticamente com base no contexto do código.

## <a name="how-to-use-it"></a>Como usá-lo

1. Coloque o cursor sobre o erro.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **Adicionar conversão explícita**.

   ![Adicionar ação rápida de conversão explícita no Visual Studio](media/add-explicit-cast.png)

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Refatoração](../refactoring-in-visual-studio.md)
