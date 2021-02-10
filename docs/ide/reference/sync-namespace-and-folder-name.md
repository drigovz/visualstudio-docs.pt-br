---
title: Sincronizar namespace e nome da pasta
description: Saiba como usar o menu ações rápidas e refatoração para sincronizar o namespace e o nome da pasta.
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e4f10f3555f4edcec031cd4c144bf5a28e9c055d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967144"
---
# <a name="sync-namespace-and-folder-name"></a>Sincronizar namespace e nome da pasta

Esta refatoração aplica-se a:

- C#

**O que:** Nome do namespace e da pasta de sincronização.

**Quando:** Você deseja rearquitetar partes de sua solução arrastando um arquivo para uma nova pasta. 

**Por que:** Você quer ter certeza de que seu namespace está atualizado com sua nova estrutura de pastas.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome do namespace.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **alterar namespace para \<folder name>**.

   ![Sincronizar namespace e nome da pasta](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
