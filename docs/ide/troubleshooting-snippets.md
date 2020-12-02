---
title: Solução de problemas de snippets
description: Saiba como solucionar problemas com trechos de código IntelliSense que geralmente são causados por conteúdo inadequado no arquivo de trecho ou um arquivo de trecho corrompido.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4012298bdc4edf0c174576c739e67781bfffdade
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479180"
---
# <a name="troubleshoot-snippets"></a>Solução de problemas de snippets

Normalmente, problemas com snippets de código IntelliSense são causados por dois problemas: um arquivo de snippet corrompido ou conteúdo inválido no arquivo de snippet.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Não é possível arrastar o snippet do Explorador de Arquivos para um arquivo de origem do Visual Studio

- Talvez o XML no arquivo de snippet esteja corrompido. O **Editor XML** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode localizar problemas na estrutura XML.

- Talvez o arquivo de snippet pode não estar em conformidade com o esquema de snippet. O **Editor XML** em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pode localizar problemas na estrutura XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>O código tem erros de compilador que não estão realçados

- Talvez esteja faltando uma referência de projeto. Examine a documentação sobre o snippet. Se a referência não for encontrada no computador, será necessário instalá-la. Inserir um snippet deve adicionar ao projeto quaisquer referências necessárias. Se o snippet estiver sem as informações de referência, isso pode ser relatado ao criador do snippet como um erro.

- Talvez uma variável esteja indefinida. Variáveis indefinidas em um snippet devem ser realçadas. Caso contrário, isso pode ser relatado ao criador do snippet como um erro.

## <a name="see-also"></a>Confira também

- [Snippets de código](../ide/code-snippets.md)
