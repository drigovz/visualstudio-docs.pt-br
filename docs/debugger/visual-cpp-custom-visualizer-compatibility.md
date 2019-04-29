---
title: Visual C /C++ compatibilidade do visualizador personalizado
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901160"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C /C++ compatibilidade do visualizador personalizado

A partir do Visual Studio de 2019, Visual C++ inclui um depurador aprimorado que usa um processo externo de 64 bits para a hospedagem de seus componentes de memória intensiva. Como parte dessa atualização, determinadas extensões para o Visual C /C++ avaliador de expressão deve ser atualizado para torná-las compatíveis com o novo depurador.

Se você atualmente está consumindo a C herdada /C++ EE addin ou C /C++ visualizador personalizado, você pode desativar o uso desse processo externo acessando **ferramentas** > **opções**  >  **Debugging**e, em seguida, desmarcando **símbolos de depuração de carga em processo externo (somente nativo)**. Se você desmarcar essa opção, ocorrerá um aumento significativo no uso de memória no processo do IDE (devenv.exe). Portanto, se você pretende depurar projetos grandes, é recomendável que você trabalhe com o proprietário da extensão para torná-lo compatível com essa opção de depuração.

Se você for o proprietário de um C herdada /C++ EE addin ou C /C++ visualizador personalizado, você pode encontrar mais informações sobre optar por carregar sua extensão em um processo de trabalho sob o [wiki de exemplos de extensibilidade Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Você também pode encontrar uma [C /C++ exemplo de visualizador personalizado](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).