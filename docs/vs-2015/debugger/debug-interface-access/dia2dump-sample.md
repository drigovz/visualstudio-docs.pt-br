---
title: Exemplo de Dia2dump | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092013"
---
# <a name="dia2dump-sample"></a>Exemplo de Dia2dump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O exemplo de Dia2dump é instalado com o Visual Studio e contém a função de origem dia2dump.cpp. O executável compilado é executado da linha de comando e exibe o conteúdo de um arquivo de banco de dados (. PDB) do programa inteiro.  
  
### <a name="to-install-the-sample"></a>Para instalar o exemplo  
  
1. Verifique se o seu sistema atende a todos os requisitos de instalação descritos a página inicial de instalação do Visual Studio.  
  
2. Instalar o Visual Studio e siga todas as instruções de instalação e configuração para os exemplos incluídos.  
  
#### <a name="to-build-the-sample"></a>Para criar o exemplo  
  
1. Abra o arquivo Dia2dump.sln no Visual Studio. (Se necessário, o Visual Studio pela primeira vez ajudará você atualizar o projeto Dia2dump.)  
  
2. Nas páginas de propriedade do projeto, nos **C/C++** &#124; **geral** &#124; **diretórios de inclusão adicionais** propriedade, especifique o `..\DIA SDK\include` directory. Isso garante que o compilador pode localizar o arquivo de dia2.h.  
  
3. No menu **Compilar**, clique em **Recompilar Solução**.  
  
4. Feche o Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra um prompt de comando e digite o seguinte:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Origem Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Como: Solucionar problemas de atualizações de projeto do Visual Studio malsucedidas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
