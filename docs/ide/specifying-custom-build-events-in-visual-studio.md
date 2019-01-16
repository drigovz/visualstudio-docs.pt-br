---
title: Especificar eventos de build personalizados
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6c5bde6b6dce7655043f3dc766a5faa81fa944e
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "53055122"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Especificar eventos de build personalizados no Visual Studio

Ao especificar um evento de build personalizado, é possível executar comandos automaticamente antes do início de um build ou após sua conclusão. Por exemplo, é possível executar um arquivo *.bat* antes do início de um build ou copiar novos arquivos para uma pasta após sua conclusão. Eventos de build serão executados somente se o build atingir com êxito esses pontos no processo de build.

 Para obter informações específicas sobre a linguagem de programação que está sendo usada, consulte os seguintes tópicos:

-   Visual Basic – [Como: Especificar eventos de build (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

-   C# e F# – [Como: Especificar eventos de build (C#)](../ide/how-to-specify-build-events-csharp.md).

-   Visual C++ – [Especificar eventos de build](/cpp/ide/specifying-build-events).

## <a name="syntax"></a>Sintaxe

Os eventos de build seguem a mesma sintaxe dos comandos do DOS, mas é possível usar macros para criar eventos de build com mais facilidade. Para obter uma lista das macros disponíveis, confira [Caixa de diálogo da linha de comando do evento de pré-build/evento de pós-build](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

 Para obter melhores resultados, siga estas dicas de formatação:

- Adicione uma instrução `call` antes de todos os eventos de build que executam arquivos *.bat*.

   Exemplo: `call C:\MyFile.bat`

   Exemplo: `call C:\MyFile.bat call C:\MyFile2.bat`

- Coloque os caminhos de arquivo entre aspas.

   Exemplo (para [!INCLUDE[win8](../debugger/includes/win8_md.md)]): “%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe” – se “$(TargetPath)”

- Separe vários comandos usando quebras de linha.

- Inclua curingas, conforme necessário.

   Exemplo: `for %I in (*.txt *.doc *.html) do copy %I c:\`*mydirectory*`\`

  > [!NOTE]
  >  `%I` no código acima deve ser `%%I` em scripts em lote.

## <a name="see-also"></a>Consulte também

- [Compilação e build](../ide/compiling-and-building-in-visual-studio.md)
- [Caixa de diálogo da linha de comando do evento de pré-build/evento de pós-build](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Caracteres especiais do MSBuild](../msbuild/msbuild-special-characters.md)
- [Passo a passo: Criar um aplicativo](../ide/walkthrough-building-an-application.md)
