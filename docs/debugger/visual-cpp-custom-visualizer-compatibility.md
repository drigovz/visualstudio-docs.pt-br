---
title: Visual C/C++ compatibilidade do visualizador personalizado
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
ms.openlocfilehash: 9fdd44be89fde2fbc26038c8b88fff405876264f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430622"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ compatibilidade do visualizador personalizado

A partir do Visual Studio 2019 C++ , o inclui um depurador aprimorado que usa um processo de 64 bits externo para hospedar seus componentes com uso intensivo de memória. Como parte dessa atualização, determinadas extensões para o avaliador CC++ /Expression devem ser atualizadas para torná-las compatíveis com o novo depurador.

Se você estiver consumindo um suplementoC++ herdado c/EE ouC++ um visualizador de c/personalizado, você poderá desativar o uso desse processo externo acessando **ferramentas** > **Opções** > **depuração**e, em seguida, desmarcando a **depuração de carga símbolos no processo externo (somente nativo)** . Se você desmarcar essa opção, ocorrerá um aumento significativo no uso da memória dentro do processo do IDE (devenv. exe). Portanto, se você espera depurar projetos grandes, é recomendável que você trabalhe com o proprietário da extensão para torná-lo compatível com essa opção de depuração.

Se você for o proprietário de um suplemento herdadoC++ do c/EE ouC++ do Visualizador de c/Custom, poderá encontrar mais informações sobre como optar por se destinar ao carregamento de sua extensão em um processo de trabalho no [wiki de exemplos de extensibilidade do Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Você também pode encontrar um [exemplo deC++ visualizador C/personalizado](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).