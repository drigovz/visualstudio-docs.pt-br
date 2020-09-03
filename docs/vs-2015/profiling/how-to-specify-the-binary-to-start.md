---
title: Como especificar o binário para iniciar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 919e84393cf4aef929a504aadbefe905afe24bfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203434"
---
# <a name="how-to-specify-the-binary-to-start"></a>Como especificar o início do binário
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para criar perfis de binários, como DLLs, você deve inserir informações na caixa de diálogo ** \<Target> páginas de propriedades** . Essa informação indica onde o projeto DLL pode localizar o aplicativo de chamada.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Para especificar o executável para iniciar  
  
1. No **Gerenciador de Desempenho**, clique com o botão direito do mouse no binário de destino e, em seguida, clique em **Propriedades**.  
  
2. Na caixa de diálogo **Páginas de Propriedades**, clique nas propriedades de **Inicialização**.  
  
3. Selecione a caixa de seleção **Substituir as propriedades de projeto**.  
  
4. Na caixa de texto **Executável a Ser Iniciado**, especifique o local do arquivo.  
  
5. Na caixa de texto **Argumentos**, especifique os argumentos que são necessários para iniciar o aplicativo.  
  
6. Na caixa de texto **Diretório de Trabalho**, especifique o local do diretório.  
  
7. Clique em **OK**.  
  
## <a name="see-also"></a>Consulte Também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)
