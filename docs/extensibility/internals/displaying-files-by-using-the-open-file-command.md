---
title: Exibir arquivos usando o comando Abrir arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c4655d251d9020c1b8b4474865126dc98fa982f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420683"
---
# <a name="display-files-by-using-the-open-file-command"></a>Exibir arquivos usando o comando Abrir arquivo
As etapas a seguir descrevem como o IDE manipula a **abrir arquivo** comando, que está disponível na **arquivo** menu no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. As etapas também descrevem como projetos devem responder a chamadas originadas desse comando.

 Quando um usuário clica o **abrir arquivo** comando as **arquivo** menu e seleciona um arquivo do **abrir arquivo** caixa de diálogo, o seguinte processo ocorre:

1. Usando a tabela de documento em execução, o IDE determina se o arquivo já está aberto em um projeto.

    - Se o arquivo estiver aberto, o IDE resurfaces a janela.

    - Se o arquivo não estiver aberto, o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para cada projeto para determinar qual projeto pode abrir o arquivo de consulta.

        > [!NOTE]
        > Na implementação do projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, forneça um valor de prioridade que indica o nível no qual seu projeto abre o arquivo. Os valores de prioridade são fornecidos no <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeração.

2. Cada projeto responde com um nível de prioridade que indica a importância coloca em que está sendo o projeto para abrir o arquivo.

3. O IDE usa os seguintes critérios para determinar qual projeto abre o arquivo:

    - O projeto que responde com a prioridade mais alta (`DP_Intrinsic`) abre o arquivo. Se mais de um projeto responder com essa prioridade, o primeiro projeto responder abre o arquivo.

    - Se nenhum projeto responde com a prioridade mais alta (`DP_Intrinsic`), mas todos os projetos de responder com a prioridade mais baixa, mesma, o projeto ativo abre o arquivo. Se nenhum projeto estiver ativo, o primeiro projeto responder abre o arquivo.

    - Se nenhum projeto declarações de propriedade do arquivo (`DP_Unsupported`), o projeto arquivos diversos abre o arquivo.

         Se uma instância do projeto arquivos diversos é criada, o projeto sempre responde com o valor `DP_CanAddAsExternal`. Esse valor indica que o projeto pode abrir o arquivo. Este projeto é usado para hospedar os arquivos abertos que não estão em qualquer outro projeto. A lista de itens neste projeto não é persistente; Este projeto está visível no **Gerenciador de soluções** somente quando ele é usado para abrir um arquivo.

         Se o projeto arquivos diversos não indicar que ele pode abrir o arquivo, uma instância do projeto não foi criada. Nesse caso, o IDE cria uma instância do projeto arquivos diversos e informa o projeto para abrir o arquivo.

4. Assim que o IDE determina qual projeto abre o arquivo, ele chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método nesse projeto.

5. O projeto, em seguida, tem a opção de abrir o arquivo usando um editor específico do projeto ou um editor padrão. Para obter mais informações, confira [Como: Abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md) e [como: Abrir editores padrão](../../extensibility/how-to-open-standard-editors.md), respectivamente.

## <a name="see-also"></a>Consulte também
- [Exibir arquivos usando o comando Abrir com](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Como: Editores abertos específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md)
- [Como: Abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)