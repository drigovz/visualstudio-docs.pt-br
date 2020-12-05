---
title: Gerar campo privado e Propriedade do Construtor
description: Saiba como usar o menu ações rápidas e refatoração para gerar um campo ou propriedade particular de um construtor.
ms.custom: SEO-VS-2020
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617455"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Gerar campo privado e Propriedade do Construtor

Esta refatoração aplica-se a: 

- C# 

**O que:** Gerar um campo ou propriedade particular de um construtor. 

**Quando:** Você deseja adicionar e inicializar rapidamente um campo ou propriedade particular de um construtor.

**Por que:** Escrever campos e propriedades particulares pode ser demorado e repetitivo. O uso dessa refatoração é rápido e torna o programa mais robusto.

## <a name="how-to"></a>Como fazer 

1. Coloque o cursor no nome do parâmetro dentro do construtor.

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
   
3. Em seguida, selecione de um dos seguintes:

- **Criar e inicializar campo** ou **criar e inicializar Propriedade**.

   ![Gerar campo particular do construtor](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Confira também 

- [Refatoração](../refactoring-in-visual-studio.md)
