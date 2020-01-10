---
title: Solução de problemas de snippets
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a699c6a158b5a0751824c7634ddd637467da50d2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588688"
---
# <a name="troubleshoot-snippets"></a>Solução de problemas de snippets

Normalmente, problemas com snippets de código IntelliSense são causados por dois problemas: um arquivo de snippet corrompido ou conteúdo inválido no arquivo de snippet.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Não é possível arrastar o snippet do Explorador de Arquivos para um arquivo de origem do Visual Studio

- Talvez o XML no arquivo de snippet esteja corrompido. O **Editor XML** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode localizar problemas na estrutura XML.

- Talvez o arquivo de snippet pode não estar em conformidade com o esquema de snippet. O **Editor XML** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode localizar problemas na estrutura XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>O código tem erros de compilador que não estão realçados

- Talvez esteja faltando uma referência de projeto. Examine a documentação sobre o snippet. Se a referência não for encontrada no computador, será necessário instalá-la. Inserir um snippet deve adicionar ao projeto quaisquer referências necessárias. Se o snippet estiver sem as informações de referência, isso pode ser relatado ao criador do snippet como um erro.

- Talvez uma variável esteja indefinida. Variáveis indefinidas em um snippet devem ser realçadas. Caso contrário, isso pode ser relatado ao criador do snippet como um erro.

## <a name="see-also"></a>Veja também

- [Snippets de código](../ide/code-snippets.md)
