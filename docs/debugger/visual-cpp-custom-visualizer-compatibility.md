---
title: Compatibilidade de visualizador personalizado do Visual C/C++
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32e38dd3bba8a1127d8756972b73e8b47a514f1b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335175"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilidade de visualizador personalizado do Visual C/C++

A partir de 2019 do Visual Studio, Visual C++ inclui um depurador aprimorado que usa um processo externo de 64 bits para a hospedagem de seus componentes de memória intensiva. Como parte dessa atualização, determinadas extensões para o avaliador de expressão do Visual C/C++ devem ser atualizados para torná-las compatíveis com o novo depurador.

Se você atualmente está consumindo um suplemento de C/C++ EE herdado ou visualizador personalizado do C/C++, você pode desativar o uso desse processo externo acessando **ferramentas** > **opções**  >   **Depurando**e, em seguida, desmarcando **símbolos de depuração de carga em processo externo (somente nativo)**. Se você desmarcar essa opção, ocorrerá um aumento significativo no uso de memória no processo do IDE (devenv.exe). Portanto, se você pretende depurar projetos grandes, é recomendável que você trabalhe com o proprietário da extensão para torná-lo compatível com essa opção de depuração.

Se você for o proprietário de um suplemento de C/C++ EE herdado ou visualizador personalizado do C/C++, você encontrará mais informações sobre optar por carregar sua extensão em um processo de trabalho sob o [exemplos de extensibilidade Concord wiki](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Você também pode encontrar uma [exemplo de visualizador personalizado do C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).