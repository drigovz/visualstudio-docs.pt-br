---
title: 'Aviso de segurança: O depurador deve executar o comando não confiável | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c57a9ce2b5a1ce9de0ffadb4b623ef3a33b8e9ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924250"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Aviso de segurança: O depurador deve executar o comando não confiável
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta caixa de diálogo de aviso aparece quando você estiver usando o servidor de origem. Indica que o comando que o depurador precisa executar para obter o código-fonte não está na lista de comandos confiáveis para o servidor de origem contido no arquivo srcsvr.ini. Se esse for um comando válido, você poderá adicioná-lo ao arquivo srcsvr.ini. Caso contrário, você não deverá executá-lo. Para obter mais informações, consulte [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Mensagem de texto  
 **O depurador deve executar o seguinte comando não confiável para obter o código-fonte do servidor de origem.**  
  
 **Se o arquivo de símbolo de depuração (\*.pdb) não for de uma origem conhecida e confiável, a execução deste comando pode ser inválida ou perigosa.**  
  
 **Você deseja executar este comando?**  
  
## <a name="uielement-list"></a>Lista UIElement  
 Caixa de texto  
 Comando do arquivo de .pdb a ser executado.  
  
 Executar  
 Permite a execução do comando.  
  
 Não execute  
 Interromper a execução de comando e fazer download do arquivo do servidor de origem.  
  
## <a name="see-also"></a>Consulte também  
 [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Servidor de Origem](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
