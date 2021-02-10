---
title: Especificar eventos de build personalizados
description: Saiba como você pode executar automaticamente comandos no Visual Studio antes que uma compilação inicie ou depois de ser concluída.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0728154e21893ac45fc0e17cc3d0407551dbb3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951024"
---
# <a name="specify-custom-build-events-in-visual-studio"></a>Especificar eventos de build personalizados no Visual Studio

Ao especificar um evento de build personalizado, é possível executar comandos automaticamente antes do início de um build ou após sua conclusão. Por exemplo, você pode executar um arquivo *. bat* antes de um Build iniciar ou copiar novos arquivos para uma pasta após a conclusão da compilação. Eventos de build serão executados somente se o build atingir com êxito esses pontos no processo de build.

Para obter informações específicas sobre a linguagem de programação que está sendo usada, consulte os seguintes tópicos:

- Visual Basic--[como especificar eventos de compilação (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).

- C# e F #--[como: especificar eventos de compilação (C#)](../ide/how-to-specify-build-events-csharp.md).

- Visual C++ – [Especificar eventos de build](/cpp/build/specifying-build-events).

## <a name="syntax"></a>Sintaxe

Os eventos de build seguem a mesma sintaxe dos comandos do DOS, mas é possível usar macros para criar eventos de build com mais facilidade. Para obter uma lista de macros disponíveis, veja [caixa de diálogo evento de pré-compilação evento/pós-compilação](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

Para obter melhores resultados, siga estas dicas de formatação:

- Adicione uma `call` instrução antes de todos os eventos de compilação que executam arquivos *. bat* .

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

- [Compilar e criar](../ide/compiling-and-building-in-visual-studio.md)
- [Caixa de diálogo linha de comando de evento de pré-compilação/evento de pós-compilação](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Caracteres especiais do MSBuild](../msbuild/msbuild-special-characters.md)
- [Passo a passo: Criar um aplicativo](../ide/walkthrough-building-an-application.md)
