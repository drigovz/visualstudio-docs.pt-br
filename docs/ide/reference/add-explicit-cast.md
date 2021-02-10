---
title: Adicionar conversão explícita
description: Saiba como adicionar automaticamente uma conversão explícita a uma expressão com base no contexto do seu código.
ms.custom: SEO-VS-2020
ms.date: 03/26/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 93365ea32ce2ad0b07b8285e3787a7a7edefffbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956653"
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
