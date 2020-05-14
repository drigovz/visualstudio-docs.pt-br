---
title: VSPackage Structure (Source Control VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703804"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estrutura do VSPackage (VSPackage de controle do código-fonte)

O SDK do Pacote de Controle de Origem fornece diretrizes para a criação de um VSPackage que permite que um implementador de controle de origem integre sua funcionalidade de controle de origem com o ambiente Visual Studio. Um VSPackage é um componente COM que normalmente é carregado sob demanda pelo Ambiente de Desenvolvimento Integrado (IDE) do Visual Studio com base nos serviços que são anunciados pelo pacote em suas entradas de registro. Cada VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>deve implementar . Um VSPackage normalmente consome serviços oferecidos pelo Visual Studio IDE e oferece alguns serviços próprios.

Um VSPackage declara seus itens de menu e estabelece um estado de item padrão através do arquivo .vsct. O Visual Studio IDE exibe os itens do menu neste estado até que o VSPackage seja carregado. Posteriormente, a implementação do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método VSPackage é chamada para ativar ou desativar itens de menu.

## <a name="source-control-package-characteristics"></a>Características do pacote de controle de origem

Um controle de origem VSPackage é profundamente integrado ao Visual Studio. A semântica VSPackage inclui:

- Interface a ser implementada em virtude de `IVsPackage` ser um VSPackage (a interface)

- Implementação do comando ui (arquivo.vsct e implementação da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface)

- Registro do VSPackage com o Visual Studio.

O controle de origem VSPackage deve se comunicar com essas outras entidades do Visual Studio:

- Projetos

- Editores

- Soluções

- Windows

- A tabela de documentos em execução

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Serviços de ambiente visual do estúdio que podem ser consumidos

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Serviço SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP implementadas e chamadas

Um pacote de controle de origem é um VSPackage e, portanto, pode interagir diretamente com outros VSPackages que estão registrados no Visual Studio. A fim de fornecer toda a amplitude da funcionalidade de controle de fonte, um controle de origem VSPackage pode lidar com interfaces fornecidas por projetos ou o shell.

Todos os projetos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual Studio devem ser implementados para serem reconhecidos como um projeto dentro do Visual Studio IDE. No entanto, esta interface não é especializada o suficiente para o controle de origem. Projetos que devem estar sob <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>controle de origem implementam . Essa interface é usada pelo controle de origem VSPackage para consultar um projeto para seu conteúdo e para fornecer glifos e informações vinculativas (as informações necessárias para estabelecer uma conexão entre a localização do servidor e a localização do disco de um projeto que está sob controle de origem).

O controle de origem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>VSPackage implementa , o que, por sua vez, permite que os projetos se registrem para controle de origem e recuperem seus glifos de status.

Para obter uma lista completa de interfaces que um controle de origem VSPackage deve considerar, consulte [Serviços e Interfaces Relacionadas](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Confira também

- [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
