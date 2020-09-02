---
title: Decisões de design de controle do código-fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705256"
---
# <a name="source-control-design-decisions"></a>Decisões de design de controle do código-fonte
As decisões de design a seguir devem ser consideradas para projetos ao implementar o controle do código-fonte.

## <a name="will-information-be-shared-or-private"></a>As informações serão compartilhadas ou privadas?
 A decisão de design mais importante que você pode fazer é que as informações são compartilháveis e o que é privado. Por exemplo, a lista de arquivos para o projeto é compartilhada, mas dentro dessa lista de arquivos, alguns usuários talvez queiram ter arquivos particulares. As configurações do compilador são compartilhadas, mas o projeto de inicialização geralmente é privado. As configurações são puramente compartilhadas, compartilhadas com uma substituição ou puramente privada. Por design, itens particulares, como arquivos de opções de usuário de solução (. suo), não são verificados [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] . Certifique-se de armazenar todas as informações particulares em arquivos particulares, como o arquivo. suo, ou um arquivo particular específico que você criar, por exemplo, um arquivo. csproj. User para Visual C# ou um arquivo. vbproj. User para Visual Basic.

 Essa decisão não é completa e pode ser feita de acordo com cada item.

## <a name="will-the-project-include-special-files"></a>O projeto incluirá arquivos especiais?
 Outra decisão de design importante é se a estrutura do projeto usa arquivos especiais. Arquivos especiais são arquivos ocultos que se baseiam nos arquivos visíveis no Gerenciador de Soluções e nas caixas de diálogo check-in e check-out. Se você usar arquivos especiais, siga estas diretrizes:

1. Não associe arquivos especiais ao nó raiz do projeto, ou seja, ao próprio arquivo do projeto. O arquivo de projeto deve ser um único arquivo.

2. Quando arquivos especiais são adicionados, removidos ou renomeados em um projeto, os eventos apropriados <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> devem ser acionados com o sinalizador definido que indica que os arquivos são arquivos especiais. Esses eventos são chamados pelo ambiente em resposta ao projeto que chama os métodos apropriados <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .

3. Quando seu projeto ou editor chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> um arquivo, os arquivos especiais associados a esse arquivo não são automaticamente submetidos a check-out. Passe os arquivos especiais junto com o arquivo pai. O ambiente detectará a relação entre todos os arquivos passados e ocultará adequadamente os arquivos especiais na interface do usuário de check-out.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Suporte para controle do código-fonte](../../extensibility/internals/supporting-source-control.md)
