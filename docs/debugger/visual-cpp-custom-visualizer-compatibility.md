---
title: Compatibilidade do visualizador personalizado do Visual C/C++
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72430622"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Compatibilidade do visualizador personalizado do Visual C/C++

A partir do Visual Studio 2019, o C++ inclui um depurador aprimorado que usa um processo de 64 bits externo para hospedar seus componentes com uso intensivo de memória. Como parte dessa atualização, determinadas extensões para o avaliador de expressões C/C++ devem ser atualizadas para torná-las compatíveis com o novo depurador.

Se estiver consumindo um suplemento herdado c/c++ EE ou um visualizador personalizado c/c++, você poderá desativar o uso desse processo externo acessando **ferramentas**  >  **Opções**  >  **depuração**e, em seguida, desmarcando a opção **carregar símbolos de depuração no processo externo (somente nativo)**. Se você desmarcar essa opção, ocorrerá um aumento significativo no uso da memória dentro do processo IDE (devenv.exe). Portanto, se você espera depurar projetos grandes, é recomendável que você trabalhe com o proprietário da extensão para torná-lo compatível com essa opção de depuração.

Se você for o proprietário de um suplemento herdado do C/C++ EE ou do visualizador personalizado C/C++, poderá encontrar mais informações sobre como optar por se destinar ao carregamento de sua extensão em um processo de trabalho no [wiki de exemplos de extensibilidade do Concord](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting). Você também pode encontrar um [exemplo de visualizador personalizado C/C++](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer).