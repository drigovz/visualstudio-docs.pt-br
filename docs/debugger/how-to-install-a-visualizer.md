---
title: Como instalar um visualizador | Microsoft Docs
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
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491310"
---
# <a name="how-to-install-a-visualizer"></a>Como instalar um visualizador
Após ter criado um visualizador, você deverá instalar o visualizador de modo que esteja disponível em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar um visualizador é um processo simples.

> [!NOTE]
> Nos aplicativos UWP, há suporte apenas para os visualizadores de texto padrão, HTML, XML e JSON. Não há suporte para visualizadores personalizados (criados pelo usuário).

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Para instalar um visualizador para o Visual Studio 2019
  
1. Localize a DLL que contém o visualizador que você criou.

2. Copie a DLL do [lado do depurador](create-custom-visualizers-of-data.md#to-create-the-debugger-side) para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copie a dll [do lado depurador](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) para qualquer um dos seguintes locais:

    - *Estrutura* de `\Common7\Packages\Debugger\Visualizers\` *VisualStudioInstallPath*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    Onde a *estrutura* é:
    - `net2.0` para depuradores que executam o tempo de execução `.NET Framework`.
    - `netstandard2.0` para depuradores usando um tempo de execução que oferece suporte a `netstandard 2.0` (`.NET Framework v4.6.1+` ou `.NET Core 2.0+`).
    - `netcoreapp` para depuradores que executam o tempo de execução `.NET Core`. (dá suporte a `.NET Core 2.0+`)

4. Reinicie a sessão de depuração.

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Para instalar um visualizador para Visual Studio 2017 e mais antigo

> [!IMPORTANT]
> Somente os visualizadores .NET Framework têm suporte no Visual Studio 2017 e mais antigos

1. Localize a DLL que contém o visualizador que você criou.

2. Copie a DLL para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Reinicie a sessão de depuração.

> [!NOTE]
> Se você quiser usar um visualizador gerenciado para a depuração remota, copie a DLL no mesmo caminho no computador remoto.

## <a name="see-also"></a>Consulte também
- [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)
- [Como escrever um visualizador](create-custom-visualizers-of-data.md)
