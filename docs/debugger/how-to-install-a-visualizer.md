---
title: 'Como: Instalar um visualizador | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9b09bc837cae4eaad2c0dbcb2bb82a7daa248eb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63389317"
---
# <a name="how-to-install-a-visualizer"></a>Como: Instalar um visualizador
Após ter criado um visualizador, você deverá instalar o visualizador de modo que esteja disponível em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar um visualizador é um processo simples.

> [!NOTE]
> Em aplicativos UWP, apenas o texto padrão, os visualizadores HTML, XML e JSON são suportados. Não há suporte para visualizadores personalizados (criados pelo usuário).

### <a name="to-install-a-visualizer"></a>Para instalar um visualizador

1. Localize a DLL que contém o visualizador que você criou.

2. Copie a DLL para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Se você quiser usar um visualizador gerenciado para a depuração remota, copie a DLL no mesmo caminho no computador remoto.

4. Reinicie a sessão de depuração.

## <a name="see-also"></a>Consulte também
- [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)
- [Como: Escrever um visualizador](/visualstudio/debugger/create-custom-visualizers-of-data)