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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3777be5701e9876352db41a5454d5e12668f6f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932111"
---
# <a name="msbuild-response-files"></a>Arquivos de resposta do MSBuild
Arquivos de resposta (*.rsp*) são arquivos de texto que contêm as opções de linha de comando do *MSBuild.exe*. Cada opção pode estar em uma linha separada ou todas as opções podem estar em uma linha. As linhas de comentários são precedidas por um símbolo **#**. A opção **@** é usada para passar outro arquivo de resposta para o *MSBuild.exe*.  
  
## <a name="msbuildrsp"></a>MSBuild.rsp
O arquivo de resposta automática é um arquivo *.rsp* especial que o *MSBuild.exe* usa automaticamente ao compilar um projeto. Esse arquivo, *MSBuild.rsp*, precisa estar no mesmo diretório do *MSBuild.exe*; caso contrário, ele não será encontrado. Edite esse arquivo para especificar opções de linha de comando padrão para o *MSBuild.exe*. Por exemplo, se você usar o mesmo agente sempre que criar um projeto, adicione a opção **-logger** a *MSBuild.rsp* e o *MSBuild.exe* usará o agente sempre que um projeto for criado. 

## <a name="directorybuildrsp"></a>Directory.Build.rsp
Na versão 15.6 e superior, o MSBuild pesquisará um arquivo chamado *Directory.Build.rsp* nos diretórios pai do projeto.  Isso pode ser útil em um repositório de código-fonte para fornecer argumentos padrão durante os builds de linha de comando.  Também pode ser usado para especificar os argumentos de linha de comando de builds hospedados. 

## <a name="see-also"></a>Consulte também  
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)