---
title: Arquivos de resposta do MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff207bdb5797cbbfb490a3b5b081ddfb1d665853
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585802"
---
# <a name="msbuild-response-files"></a>Arquivos de resposta do MSBuild
Arquivos de resposta ( *.rsp*) são arquivos de texto que contêm as opções de linha de comando do *MSBuild.exe*. Cada opção pode estar em uma linha separada ou todas as opções podem estar em uma linha. As linhas de comentários são precedidas por um símbolo **#** . A opção **@** é usada para passar outro arquivo de resposta para o *MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp
O arquivo de resposta automática é um arquivo *.rsp* especial que o *MSBuild.exe* usa automaticamente ao compilar um projeto. Esse arquivo, *MSBuild.rsp*, precisa estar no mesmo diretório do *MSBuild.exe*; caso contrário, ele não será encontrado. Edite esse arquivo para especificar opções de linha de comando padrão para o *MSBuild.exe*. Por exemplo, se você usar o mesmo agente sempre que criar um projeto, adicione a opção **-logger** a *MSBuild.rsp* e o *MSBuild.exe* usará o agente sempre que um projeto for criado.

## <a name="directorybuildrsp"></a>Directory.Build.rsp
Na versão 15.6 e superior, o MSBuild pesquisará um arquivo chamado *Directory.Build.rsp* nos diretórios pai do projeto.  Isso pode ser útil em um repositório de código-fonte para fornecer argumentos padrão durante os builds de linha de comando.  Também pode ser usado para especificar os argumentos de linha de comando de builds hospedados.

## <a name="see-also"></a>Veja também
- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)
