---
title: Sincronizar namespace e nome da pasta
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d7073edaf6ecc261c58bf1e5607323b9214c5ed0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67160752"
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
3. Selecione **alterar namespace para \<folder name> **.

   ![Sincronizar namespace e nome da pasta](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
