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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197593"
---
# <a name="dia2dump-sample"></a>Exemplo de Dia2dump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O exemplo Dia2dump é instalado com o Visual Studio e contém o arquivo de origem Dia2dump. cpp. O executável compilado é executado na linha de comando e exibe o conteúdo de um arquivo de banco de dados do programa inteiro (. pdb).  
  
### <a name="to-install-the-sample"></a>Para instalar o exemplo  
  
1. Verifique se o sistema atende a todos os requisitos de instalação descritos na página inicial da instalação do Visual Studio.  
  
2. Instale o Visual Studio e siga todas as instruções de instalação e instalação para os exemplos incluídos.  
  
#### <a name="to-build-the-sample"></a>Para criar o exemplo  
  
1. Abra o arquivo Dia2dump. sln no Visual Studio. (Se necessário, o Visual Studio irá ajudá-lo primeiro a atualizar o projeto Dia2dump.)  
  
2. Nas páginas de propriedades do projeto, na propriedade **C/C++** &#124; **geral** &#124; **diretórios de inclusão adicionais** , especifique o `..\DIA SDK\include` diretório. Isso garante que o compilador possa localizar o arquivo dia2. h.  
  
3. No menu **Compilar**, clique em **Recompilar Solução**.  
  
4. Feche o Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra um prompt de comando e digite o seguinte:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Consulte Também  
 [Arquivo de origem Dia2dump. cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Como solucionar problemas de atualizações de projeto do Visual Studio malsucedidas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
