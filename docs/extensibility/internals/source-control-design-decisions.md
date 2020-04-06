---
title: Decisões de design de controle de fonte | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705256"
---
# <a name="source-control-design-decisions"></a>Decisões de design de controle do código-fonte
As seguintes decisões de projeto devem ser consideradas para projetos na implementação do controle de origem.

## <a name="will-information-be-shared-or-private"></a>As informações serão compartilhadas ou privadas?
 A decisão de design mais importante que você pode tomar é o que a informação é escassa e o que é privado. Por exemplo, a lista de arquivos para o projeto é compartilhada, mas dentro desta lista de arquivos, alguns usuários podem querer ter arquivos privados. As configurações do compilador são compartilhadas, mas o projeto de inicializar é geralmente privado. As configurações são puramente compartilhadas, compartilhadas com uma substituição ou puramente privadas. Pelo design, itens privados, como arquivos de opções de usuário de [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]solução (.suo), não são verificados . Certifique-se de armazenar qualquer informação privada em arquivos privados, como o arquivo .suo ou um arquivo privado específico que você cria, por exemplo, um arquivo .csproj.user para Visual C# ou um arquivo .vbproj.user para Visual Basic.

 Esta decisão não é all-inclusive e pode ser tomada em uma base item por item.

## <a name="will-the-project-include-special-files"></a>O projeto incluirá arquivos especiais?
 Outra decisão importante do projeto é se sua estrutura de projeto usa arquivos especiais. Arquivos especiais são arquivos ocultos que sustentam os arquivos que são visíveis no Solution Explorer e nas caixas de diálogo de check-in e check-out. Se você usar arquivos especiais, siga estas diretrizes:

1. Não associe arquivos especiais ao nó raiz do projeto — ou seja, com o próprio arquivo do projeto. Seu arquivo de projeto deve ser um único arquivo.

2. Quando arquivos especiais são adicionados, removidos ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> renomeados em um projeto, os eventos apropriados devem ser acionados com o conjunto de sinalizadores que indica que os arquivos são arquivos especiais. Esses eventos são chamados pelo meio ambiente em <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> resposta ao projeto chamando os métodos apropriados.

3. Quando seu projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ou editor pede um arquivo, os arquivos especiais associados a esse arquivo não são automaticamente verificados. Passe os arquivos especiais junto com o arquivo pai. O ambiente detectará a relação entre todos os arquivos que são passados e ocultará adequadamente os arquivos especiais na ui check-out.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Suporte para controle do código-fonte](../../extensibility/internals/supporting-source-control.md)
