---
title: 'Aviso: a dependência &#39;arquivo&#39; no projeto &#39;projeto&#39; não pode ser copiado para o diretório de execução porque ela substituiria a referência de &#39;arquivo. &#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d2f2a70df72f6dfcdc8946ca2f5afec9efa21a65
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934427"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>Aviso: a dependência &#39;arquivo&#39; no projeto &#39;projeto&#39; não pode ser copiado para o diretório de execução porque ela substituiria a referência de &#39;arquivo.&#39;
Há um conflito entre as dependências; mais de um arquivo de assembly distintos com o mesmo nome deve ser copiados para o diretório bin para a execução do aplicativo. O diretório de execução é capaz de resolver o conflito, pois uma das dependências é uma referência primária.  
  
 Clicar duas vezes neste item de lista de tarefas, você serão levado para o nó de referência principal que está em conflito.  
  
 Este aviso ocorre quando você tem um conflito de dependência, mas tê contornado através da adição de uma das dependências conflitantes como uma referência. Ou você pode ter tido uma referência de versão 1 e, em seguida, adicionei uma referência a segunda que se faz referência a versão 2 da referência primeiro.  
  
 Ou seja, esse erro ocorre porque os projetos em sua solução têm referências entre si, mas as referências foram criadas como referências de arquivo (usando o **navegue** botão na [adicionar referência](http://msdn.microsoft.com/2feb0fe2-0805-4cc9-8cba-b0315849dfb7) caixa de diálogo caixa), em vez de referências projeto a projeto (usando o **Project** guia o **adicionar referência** caixa de diálogo). A vantagem de uma referência projeto a projeto é que ele cria uma dependência entre os projetos no sistema de build para que o projeto dependente será compilado se ele foi alterado desde a última vez em que o projeto de referência foi criado. Uma referência de arquivo não cria uma dependência de build para que seja possível compilar o projeto de referência sem compilar o projeto dependente, e, portanto, uma referência pode se tornar obsoleta; um projeto pode referenciar uma versão anteriormente compilada do projeto. Isso pode resultar em várias versões de uma única DLL seja necessária no diretório bin, o que não é possível e resulta nessa mensagem de erro.  
  
 Esta mensagem é exibida sempre que houver um conflito no diretório bin e o aplicativo pode não funcionar corretamente. Mesmo que você pode ter trabalhado alternativa para esse problema, esse aviso ainda aparecerá, pois o sistema de projeto não é possível determinar se a versão de uma dependência funcionará corretamente com todos os componentes.  
  
 **Para corrigir este erro**  
  
- Copie arquivos de assembly de um (ou zero) para o diretório bin, que pode ser feito colocando os arquivos de assembly no cache de assembly global. O cache de assembly global resolve conflitos de nome de arquivo. Não será feita nenhuma cópia local do arquivo assembly porque o common language runtime sabe como localizar assemblies no cache de assembly global. Para obter mais informações, consulte [trabalhando com Assemblies e Cache de Assembly Global](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433) e [erro: a dependência 'arquivo' no projeto 'projeto' não pode ser copiada para o diretório de execução porque ela entraria em conflito com a dependência ' arquivo '](/visualstudio/misc/error-dependency-file?view=vs-2015).  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [Cache de assembly global](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Como: criar e remover dependências de projeto](../ide/how-to-create-and-remove-project-dependencies.md)