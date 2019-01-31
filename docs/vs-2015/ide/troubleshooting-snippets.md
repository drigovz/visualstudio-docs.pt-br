---
title: Solucionando problemas de snippets | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7fe80ad6c3983b35f97071093428bf7f356292b0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803756"
---
# <a name="troubleshooting-snippets"></a>Solucionando problemas de snippets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Normalmente, problemas com snippets de código IntelliSense são causados por dois problemas: um arquivo de snippet corrompido ou conteúdo inválido no arquivo de snippet.  
  
## <a name="common-problems"></a>Problemas comuns  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>O snippet não pode ser arrastado do Explorador de Arquivos para um arquivo de origem do Visual Studio  
  
-   Talvez o XML no arquivo de snippet esteja corrompido. O **Editor XML** em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pode localizar problemas na estrutura XML.  
  
-   Talvez o arquivo de snippet pode não estar em conformidade com o esquema de snippet. O **Editor XML** em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pode localizar problemas na estrutura XML.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>O código tem erros de compilador que não estão realçados  
  
-   Talvez esteja faltando uma referência de projeto. Examine a documentação sobre o snippet. Se a referência não for encontrada no computador, será necessário instalá-la. Inserir um snippet deve adicionar ao projeto quaisquer referências necessárias. Se o snippet estiver sem as informações de referência, isso pode ser relatado ao criador do snippet como um erro.  
  
-   Talvez uma variável esteja indefinida. Variáveis indefinidas em um snippet devem ser realçadas. Caso contrário, isso pode ser relatado ao criador do snippet como um erro.  
  
## <a name="see-also"></a>Consulte também  
 [Snippets de código](../ide/code-snippets.md)
