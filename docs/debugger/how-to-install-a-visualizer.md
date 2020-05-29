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
ms.openlocfilehash: c79fd5522447378b879443eb8dccabfe7081af4f
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183620"
---
# <a name="how-to-install-a-visualizer"></a>Como instalar um visualizador
Após ter criado um visualizador, você deverá instalar o visualizador de modo que esteja disponível em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar um visualizador é um processo simples.

> [!NOTE]
> Nos aplicativos UWP, há suporte apenas para os visualizadores de texto padrão, HTML, XML e JSON. Não há suporte para visualizadores personalizados (criados pelo usuário).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Para instalar um visualizador para o Visual Studio 2019
  
1. Localize a DLL que contém o visualizador que você criou.

   Normalmente, é melhor se a DLL do lado do depurador e a DLL do lado do depurador especificarem **qualquer CPU** como a plataforma de destino. A DLL do lado do depurador deve ser **qualquer CPU** ou **32 bits**. A plataforma de destino para a DLL do lado do depurador deve corresponder ao processo do depurador.

2. Copie a DLL do [lado do depurador](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (e quaisquer DLLs das quais ela depende) para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copie a dll [do lado depurador](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Estrutura*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Estrutura*

    onde a *estrutura* é:
    - `net2.0`para depuradores que executam o `.NET Framework` tempo de execução.
    - `netstandard2.0`para os depuradores que usam um tempo de execução que dá suporte a `netstandard 2.0` ( `.NET Framework v4.6.1+` ou `.NET Core 2.0+` ).
    - `netcoreapp`para depuradores que executam o `.NET Core` tempo de execução. (dá suporte a `.NET Core 2.0+` )

4. Reinicie a sessão de depuração.

> [!NOTE]
> O procedimento é diferente no Visual Studio 2017 e mais antigo. Consulte a [versão anterior](how-to-install-a-visualizer.md?view=vs-2017) deste artigo.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Para instalar um visualizador para Visual Studio 2017 e mais antigo

> [!IMPORTANT]
> Somente os visualizadores .NET Framework têm suporte no Visual Studio 2017 e mais antigos.

1. Localize a DLL que contém o visualizador que você criou.

2. Copie a DLL para qualquer um dos seguintes locais:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Reinicie a sessão de depuração.

> [!NOTE]
> Se você quiser usar um visualizador gerenciado para a depuração remota, copie a DLL no mesmo caminho no computador remoto.
::: moniker-end

## <a name="see-also"></a>Veja também
- [Criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)
- [Como escrever um visualizador](create-custom-visualizers-of-data.md)
