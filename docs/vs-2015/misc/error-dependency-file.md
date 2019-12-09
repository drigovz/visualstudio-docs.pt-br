---
title: 'Erro: o arquivo &#39;&#39; de dependência no &#39;projeto&#39; de projeto não pode ser copiado para o diretório de execução porque &#39;ele&#39; estaria em conflito com o arquivo de dependência | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4fd45741585aaf82c82257999b40d6257e82d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656041"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Erro: o arquivo &#39;&#39; de dependência no &#39;projeto&#39; de projeto não pode ser copiado para o diretório de execução porque &#39;estaria em conflito com o arquivo de dependência&#39;
Há um conflito entre referências; mais de uma dependência distinta com o mesmo nome de arquivo que está sendo copiado para o diretório bin para que o aplicativo seja executado. O diretório de execução não pode resolver o conflito porque nenhuma das dependências são referências primárias.

 Esse erro fará com que a compilação falhe.

 Clicar duas vezes nesse Lista de Tarefas item o levará para o nó referências do projeto no qual o conflito está ocorrendo.

 **Para corrigir esse erro**

- Torne um dos assemblies uma referência direta do seu projeto. Uma possível desvantagem dessa abordagem é que o assembly escolhido não tem garantia de trabalhar com assemblies que exigem alguma outra versão do assembly referenciado.

     \- ou -

- Certifique-se de que ambas as cópias do assembly sejam de nome forte e no cache de assembly global. Isso elimina a necessidade de copiar os assemblies para o diretório bin.

## <a name="see-also"></a>Consulte também
 [Gerenciamento de referências em um projeto de](../ide/managing-references-in-a-project.md) [assembly global](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) [assemblies com nome forte](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [assembly controle de versão](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [como criar e remover dependências de projeto](../ide/how-to-create-and-remove-project-dependencies.md)