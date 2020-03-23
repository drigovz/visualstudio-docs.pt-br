---
title: Especificar eventos de build personalizados
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fda60ffb97ecb44bd4a881cb42e4d9199cc958b8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115332"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Especificar eventos de build personalizados no Visual Studio

Ao especificar um evento de build personalizado, é possível executar comandos automaticamente antes do início de um build ou após sua conclusão. Por exemplo, você pode executar um arquivo *.bat* antes que uma compilação seja iniciada ou copie novos arquivos para uma pasta depois que a compilação estiver concluída. Eventos de build serão executados somente se o build atingir com êxito esses pontos no processo de build.

Para obter informações específicas sobre a linguagem de programação que está sendo usada, consulte os seguintes tópicos:

- Visual Basic -[Como: Especificar eventos de construção (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# e F#--[Como: Especificar eventos de construção (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++ – [Especificar eventos de build](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Sintaxe

Os eventos de build seguem a mesma sintaxe dos comandos do DOS, mas é possível usar macros para criar eventos de build com mais facilidade. Para obter uma lista de macros disponíveis, consulte Caixa de diálogo de linha de diálogo de linha de diálogo de [evento pré-build/post-build Event](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Para obter melhores resultados, siga estas dicas de formatação:

- Adicione `call` uma declaração antes de todos os eventos de compilação que executam arquivos *.bat.*

   Exemplo: `call C:\MyFile.bat`

   Exemplo: `call C:\MyFile.bat call C:\MyFile2.bat`

- Coloque os caminhos de arquivo entre aspas.

   Exemplo (para [!INCLUDE[win8](../debugger/includes/win8_md.md)]): “%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe” – se “$(TargetPath)”

- Separe vários comandos usando quebras de linha.

- Inclua curingas, conforme necessário.

   Exemplo: `for %I in (*.txt *.doc *.html) do copy %I c:\` *mydirectory*`\`

  > [!NOTE]
  > `%I` no código acima deve ser `%%I` em scripts em lote.

## <a name="see-also"></a>Confira também

- [Compilação e construção](../ide/compiling-and-building-in-visual-studio.md)
- [Caixa de diálogo de diálogo de linha de diálogo de linha de diálogo de linha de diálogo de linha de diálogo de evento de pré-compilação/pós-compilação de eventos](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [MSBuild caracteres especiais](../msbuild/msbuild-special-characters.md)
- [Passo a passo: Criar um aplicativo](../ide/walkthrough-building-an-application.md)
