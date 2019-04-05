---
title: Exibir arquivos usando o comando Abrir arquivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 286f310765db6fff14f6b134c6107ff1c9e36215
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929670"
---
# <a name="displaying-files-by-using-the-open-file-command"></a>Exibindo arquivos usando o comando Abrir Arquivo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

As etapas a seguir descrevem como o IDE manipula a **abrir arquivo** comando, que está disponível na **arquivo** menu no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. As etapas também descrevem como projetos devem responder a chamadas originadas desse comando.  
  
 Quando um usuário clica o **abrir arquivo** comando as **arquivo** menu e seleciona um arquivo do **abrir arquivo** caixa de diálogo, o seguinte processo ocorre.  
  
1.  Usando a tabela de documento em execução, o IDE determina se o arquivo já está aberto em um projeto.  
  
    -   Se o arquivo estiver aberto, o IDE resurfaces a janela.  
  
    -   Se o arquivo não estiver aberto, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para cada projeto para determinar qual projeto pode abrir o arquivo de consulta.  
  
        > [!NOTE]
        >  Na implementação do projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, forneça um valor de prioridade que indica o nível no qual seu projeto abre o arquivo. Os valores de prioridade são fornecidos no <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeração.  
  
2.  Cada projeto responde com um nível de prioridade que indica a importância coloca em que está sendo o projeto para abrir o arquivo.  
  
3.  O IDE usa os seguintes critérios para determinar qual projeto abre o arquivo:  
  
    -   O projeto que responde com a prioridade mais alta (DP_Intrinsic) abre o arquivo. Se mais de um projeto responder com essa prioridade, o primeiro projeto responder abre o arquivo.  
  
    -   Se nenhum responde de projeto com a prioridade mais alta (DP_Intrinsic), mas responder de todos os projetos com a mesma, com baixa prioridade, o projeto ativo abre o arquivo. Se nenhum projeto estiver ativo, o primeiro projeto responder abre o arquivo.  
  
    -   Se nenhum projeto declarações de propriedade do arquivo (DP_Unsupported), o projeto arquivos diversos abre o arquivo.  
  
         Se uma instância do projeto arquivos diversos é criada, o projeto sempre responde com o valor DP_CanAddAsExternal. Esse valor indica que o projeto pode abrir o arquivo. Este projeto é usado para hospedar os arquivos abertos que não estão em qualquer outro projeto. A lista de itens neste projeto não é persistente; Este projeto está visível no **Gerenciador de soluções** somente quando ele é usado para abrir um arquivo.  
  
         Se o projeto arquivos diversos não indicar que ele pode abrir o arquivo, uma instância do projeto não foi criada. Nesse caso, o IDE cria uma instância do projeto arquivos diversos e informa o projeto para abrir o arquivo.  
  
4.  Assim que o IDE determina qual projeto abre o arquivo, ele chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método nesse projeto.  
  
5.  O projeto, em seguida, tem a opção de abrir o arquivo usando um editor específico do projeto ou um editor padrão. Para obter mais informações, confira [Como: Abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md) e [como: Abrir editores padrão](../../extensibility/how-to-open-standard-editors.md), respectivamente.  
  
## <a name="see-also"></a>Consulte também  
 [Exibir arquivos usando o aberto com o comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Como: Editores abertos específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Como: Abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
