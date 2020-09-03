---
title: 'Aviso: o&#39; de arquivo de dependência &#39;no projeto &#39;projeto&#39; não pode ser copiado para o diretório de execução porque ele substituiria o arquivo de &#39;de referência. &#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a619168bd07fde5d27e5c3d87dc46f505cf5268d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672815"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Aviso: o&#39; de arquivo de dependência &#39;no projeto &#39;projeto&#39; não pode ser copiado para o diretório de execução porque ele substituiria o arquivo de &#39;de referência. &#39;
Há um conflito entre dependências; mais de um arquivo de assembly distinto com o mesmo nome devem ser copiados para o diretório bin para que o aplicativo seja executado. O diretório de execução é capaz de resolver o conflito, pois uma das dependências é uma referência principal.

 Clicar duas vezes nesse Lista de Tarefas item levará você para o nó de referência principal que está em conflito.

 Esse aviso ocorre quando você tem um conflito de dependência, mas trabalhou em lugar dele adicionando uma das dependências conflitantes como referência. Ou talvez você tenha tido uma referência da versão 1 e, em seguida, adicionou uma segunda referência que, por sua vez, faz referência à versão 2 da primeira referência.

 Ou seja, esse erro ocorre porque os projetos em sua solução têm referências entre si, mas as referências foram criadas como referências de arquivo (usando o botão **procurar** na caixa de diálogo [Adicionar referência](https://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) ), em vez de projeto para referências de projeto (usando a guia **projeto** na caixa de diálogo **Adicionar referência** ). A vantagem de uma referência de projeto para projeto é que ele cria uma dependência entre os projetos no sistema de compilação para que o projeto dependente seja criado se ele foi alterado desde a última vez que o projeto de referência foi criado. Uma referência de arquivo não cria uma dependência de compilação, portanto, é possível criar o projeto de referência sem compilar o projeto dependente e, portanto, uma referência pode se tornar obsoleta; um projeto pode fazer referência a uma versão criada anteriormente do projeto. Isso pode resultar em várias versões de uma única DLL sendo necessária no diretório bin, o que não é possível e resulta nessa mensagem de erro.

 Essa mensagem é exibida toda vez que há um conflito no diretório bin e o aplicativo pode não funcionar corretamente. Embora você possa ter solucionado esse problema, esse aviso ainda aparecerá porque o sistema do projeto não pode determinar se a versão de uma dependência funcionará corretamente com todos os componentes.

 **Para corrigir esse erro**

- Copie um (ou zero) arquivos de assembly para o diretório bin, que pode ser feito colocando os arquivos de assembly no cache de assembly global. O cache de assembly global resolve conflitos de nome de arquivo. Nenhuma cópia local do arquivo de assembly será feita porque o Common Language Runtime sabe como encontrar assemblies no cache de assembly global. Para obter mais informações, consulte [trabalhando com assemblies e o cache de assembly global](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) e [erro: a dependência ' file ' no projeto ' Project ' não pode ser copiada para o diretório de execução porque estaria em conflito com a dependência ' file '](/visualstudio/misc/error-dependency-file?view=vs-2015).

## <a name="see-also"></a>Consulte Também
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md) [cache de assembly global](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) [como: criar e remover dependências de projeto](../ide/how-to-create-and-remove-project-dependencies.md)