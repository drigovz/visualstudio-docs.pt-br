---
title: Caixa de diálogo de páginas de propriedade do código-fonte arquivos, propriedades comuns, solução de depuração | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47fb2511e39153753a2c27483dd6ac96c26c9e83
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925142"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Caixa de diálogo Depurar Arquivos de Origem, Propriedades Comuns, Páginas de Propriedades da Solução
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta página de propriedades especifica onde o depurador procurará arquivos de origem ao depurar a solução.  
  
 Para acessar a página de propriedades **Depurar Arquivos de Origem**, clique com o botão direito do mouse na solução em **Gerenciador de Soluções** e selecione **Propriedades** no menu de atalho. Expanda a pasta **Propriedades Comuns** e clique na página **Depurar Arquivos de Origem**.  
  
 **Diretórios que contêm o código-fonte**  
 Contém uma lista de diretórios nos quais o depurador procura arquivos de origem ao depurar a solução. Os subdiretórios dos diretórios especificados também são pesquisados.  
  
 **Não procurar por estes arquivos de origem**  
 Insira os nomes de todos os arquivos que você não deseja que o depurador leia. Se o depurador encontrar um desses arquivos em um dos diretórios especificados acima, ele o ignorará. Se a caixa de diálogo **Localizar Fonte** aparecer durante a depuração e você clicar em **Cancelar**, o arquivo que você procurava será adicionado a essa lista para que o depurador não continue a procurar o arquivo.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)
