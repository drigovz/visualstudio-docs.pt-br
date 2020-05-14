---
title: Exibindo arquivos usando o comando Arquivo Aberto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708591"
---
# <a name="display-files-by-using-the-open-file-command"></a>Exibir arquivos usando o comando Abrir arquivo
As etapas a seguir descrevem como o IDE lida com o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comando Arquivo **Aberto,** que está disponível no menu **Arquivo** em . As etapas também descrevem como os projetos devem responder a chamadas originárias deste comando.

 Quando um usuário clica no comando **Abrir arquivo** no menu **Arquivo** e seleciona um arquivo na caixa de diálogo **Arquivo Aberto,** ocorre o seguinte processo:

1. Usando a tabela de documentos em execução, o IDE determina se o arquivo já está aberto em um projeto.

    - Se o arquivo estiver aberto, o IDE ressurgirá a janela.

    - Se o arquivo não estiver aberto, o IDE chamará <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para consultar cada projeto para determinar qual projeto pode abrir o arquivo.

        > [!NOTE]
        > Na implementação <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>do projeto, forneça um valor prioritário que indique o nível em que seu projeto abre o arquivo. Os valores prioritários <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> são fornecidos na enumeração.

2. Cada projeto responde com um nível de prioridade que indica a importância que ele coloca em ser o projeto para abrir o arquivo.

3. O IDE usa os seguintes critérios para determinar qual projeto abre o arquivo:

    - O projeto que responde com a`DP_Intrinsic`maior prioridade ( ) abre o arquivo. Se mais de um projeto responder com essa prioridade, o primeiro projeto a responder abre o arquivo.

    - Se nenhum projeto responder com a`DP_Intrinsic`maior prioridade ( ), mas todos os projetos respondem com a mesma, menor prioridade, o projeto ativo abre o arquivo. Se nenhum projeto estiver ativo, o primeiro projeto a responder abre o arquivo.

    - Se nenhum projeto reivindicar a`DP_Unsupported`propriedade do arquivo (), o projeto Arquivos Diversos abrirá o arquivo.

         Se uma instância do projeto Arquivos Diversos for criada, o projeto sempre responderá com o valor `DP_CanAddAsExternal`. Esse valor indica que o projeto pode abrir o arquivo. Este projeto é usado para abrigar arquivos abertos que não estão em nenhum outro projeto. A lista de itens deste projeto não é persistiu; este projeto só é visível no **Solution Explorer** quando ele é usado para abrir um arquivo.

         Se o projeto Arquivos Diversos não indicar que ele pode abrir o arquivo, uma instância do projeto não foi criada. Neste caso, o IDE cria uma instância do projeto Arquivos Diversos e diz ao projeto para abrir o arquivo.

4. Assim que o IDE determinar qual projeto abre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> o arquivo, ele chama o método nesse projeto.

5. O projeto então tem a opção de abrir o arquivo usando um editor específico do projeto ou um editor padrão. Para obter mais informações, consulte [Como: Abrir editores específicos do projeto](../../extensibility/how-to-open-project-specific-editors.md) [e como: Abrir editores padrão,](../../extensibility/how-to-open-standard-editors.md)respectivamente.

## <a name="see-also"></a>Confira também
- [Exibir arquivos usando o comando Abrir com](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Abrir e salvar itens do projeto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Como: Abrir editores específicos de projetos](../../extensibility/how-to-open-project-specific-editors.md)
- [Como: Abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)
