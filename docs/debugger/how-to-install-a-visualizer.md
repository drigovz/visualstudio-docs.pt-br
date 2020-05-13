---
title: 'Como: Instalar um Visualizador | Microsoft Docs'
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
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880254"
---
# <a name="how-to-install-a-visualizer"></a>Como instalar um visualizador
Após ter criado um visualizador, você deverá instalar o visualizador de modo que esteja disponível em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar um visualizador é um processo simples.

> [!NOTE]
> Nos aplicativos UWP, apenas os visualizadores padrão de texto, HTML, XML e JSON são suportados. Não há suporte para visualizadores personalizados (criados pelo usuário).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Para instalar um visualizador para o Visual Studio 2019
  
1. Localize o DLL que contém o visualizador que você construiu.

   Normalmente, é melhor que tanto o DLL do lado do depurador quanto o DLL do lado da depuração especifiquem **qualquer CPU** como plataforma de destino. O DLL do lado do depurador deve ser **qualquer CPU** ou **32 bits**. A plataforma de destino da DLL do lado da depuração deve corresponder ao processo de depuração.

2. Copie o [DLL lateral de depuração](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (e quaisquer DLLs que dependam) para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copie o DLL do lado de [depuração](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Framework*

    onde *o Framework* é:
    - `net2.0`para depurações em `.NET Framework` execução do tempo de execução.
    - `netstandard2.0`para depurações usando um tempo `netstandard 2.0` de`.NET Framework v4.6.1+` `.NET Core 2.0+`execução que suporta (ou ).
    - `netcoreapp`para depurações em `.NET Core` execução do tempo de execução. (suportes) `.NET Core 2.0+`

4. Reinicie a sessão de depuração.

> [!NOTE]
> O procedimento é diferente no Visual Studio 2017 e mais antigo. Veja a [versão anterior](how-to-install-a-visualizer.md?view=vs-2017) deste artigo.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Para instalar um visualizador para visual Studio 2017 e mais antigo

> [!IMPORTANT]
> Apenas os visualizadores .NET Framework são suportados no Visual Studio 2017 e mais antigos.

1. Localize a DLL que contém o visualizador que você criou.

2. Copie a DLL para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Reinicie a sessão de depuração.

> [!NOTE]
> Se você quiser usar um visualizador gerenciado para a depuração remota, copie a DLL no mesmo caminho no computador remoto.
::: moniker-end

## <a name="see-also"></a>Confira também
- [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)
- [Como escrever um visualizador](create-custom-visualizers-of-data.md)
