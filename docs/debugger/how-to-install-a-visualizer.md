---
title: 'Como: instalar um visualizador | Microsoft Docs'
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
ms.openlocfilehash: d1a552c07443e4dd38070a86b7d9513d8cfa0136
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691417"
---
# <a name="how-to-install-a-visualizer"></a>Como instalar um visualizador
Após ter criado um visualizador, você deverá instalar o visualizador de modo que esteja disponível em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar um visualizador é um processo simples.

> [!NOTE]
>  Em aplicativos UWP, apenas o texto padrão, os visualizadores HTML, XML e JSON são suportados. Não há suporte para visualizadores personalizados (criados pelo usuário).

### <a name="to-install-a-visualizer"></a>Para instalar um visualizador

1.  Localize a DLL que contém o visualizador que você criou.

2.  Copie a DLL para qualquer um dos seguintes locais:

    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    -   `My Documents\` *VisualStudioVersion* `\Visualizers`

3.  Se você quiser usar um visualizador gerenciado para a depuração remota, copie a DLL no mesmo caminho no computador remoto.

4.  Reinicie a sessão de depuração.

## <a name="see-also"></a>Consulte também
- [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)
- [Como escrever um visualizador](/visualstudio/debugger/create-custom-visualizers-of-data)