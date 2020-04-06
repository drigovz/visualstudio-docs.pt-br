---
title: Serviços e interfaces relacionados (Source Control VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705621"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>Serviços e interfaces relacionados (VSPackage de controle do código-fonte)
Esta seção lista todas as interfaces relacionadas ao vspackage de controle de origem no [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]. O controle de origem VSPackage implementa algumas dessas interfaces e usa outras para realizar tarefas de controle de origem.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>Interfaces implementadas por e para vspackages de controle de fonte
 As seguintes interfaces [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]são descritas no , e o controle de origem VSPackage implementa um subconjunto deles dependendo do conjunto de recursos desejado. Algumas interfaces são marcadas conforme necessário e devem ser implementadas por todos os vsPackage de controle de origem.

 Para essas interfaces que um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacote não implementa, fornece uma implementação padrão. Observe que a implementação padrão foi projetada para o caso quando nenhum VSPackage está registrado e nenhum projeto é controlado. Um controle de origem devidamente escrito VSPackage implementa todas as interfaces necessárias em vez de deixá-la para a implementação padrão dessas interfaces.

 Um controle de origem VSPackage deve implementar um serviço privado que encapsula algumas ou todas as interfaces a seguir.

 As interfaces são:

- Obrigatório: A entidade apropriada (controle de origem VSPackage, Source Control Stub, project) deve implementar a interface.

- Recomendado: A entidade deve implementar esta interface; caso contrário, a funcionalidade de controle de origem pode ser limitada.

- Opcional: a entidade pode implementar essa interface para fornecer um conjunto de recursos mais rico.

| Interface | Finalidade | Implementado por | Implementar? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | Os editores chamam essa interface antes de modificar ou salvar um arquivo. O controle de origem VSPackage pode verificar o arquivo ou negar a operação se o checkout falhar. | Controle de origem VSPackage | Recomendadas |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | Essa interface fornece funcionalidade básica de controle de origem para projetos, como registrar e cancelar projetos com controle de origem e fornecer suporte para glifos básicos de controle de origem. | Controle de origem VSPackage | Obrigatório |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | Esta interface é obtida <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> a <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> partir do uso da função, ou simplesmente lançando o objeto implementando `IVsHierarchy` para `IVsSccProject2`. Ele é usado para obter os arquivos sob controle de origem em um projeto ou para informar o projeto do status ou localização de controle de origem atual. | Project | Obrigatório |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | O módulo de integração usa esta interface para definir o VSPackage ativo atual. | Controle de origem VSPackage | Obrigatório |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | Esta interface é baseada em um modelo de assinatura. Qualquer VSPackage pode sinalizar que deseja receber eventos de documentos e ser avisado pela shell sobre eventos que estão prestes a acontecer. Ele é implementado e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]manuseado por , `IVsTrackProjectDocumentsEvents2` que por sua vez passa eventos implementando o para o VSPackage. | Stub de controle de origem | Obrigatório |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | Essa interface fornece processamento em lote, operações sincronizadas de leitura/gravação e um método avançado. `OnQueryAddFiles` | Stub de controle de origem | Obrigatório |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **O Solution Explorer** e os projetos chamam essa interface quando novos arquivos são adicionados aos projetos ou quando arquivos e pastas são renomeados ou excluídos de projetos. O controle de origem VSPackage pode verificar o arquivo do projeto ou cancelar a operação. | Controle de origem VSPackage | Recomendadas |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **O Solution Explorer** e os projetos chamam essa interface em resposta às chamadas feitas aos métodos da interface IVstrackProjectDocuments3. O controle de origem VSPackage pode acompanhar operações em lote, operações sincronizadas de leitura/gravação e trabalhar com um método mais avançado. `OnQueryAddFiles` | Controle de origem VSPackage | Recomendadas |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | Esta interface fornece suporte de gerenciamento de alistamento para projetos web. | Controle de origem VSPackage | Recomendadas |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | Esta interface é usada para recuperar dicas de ferramentas para os arquivos controlados por origem nos projetos. | Controle de origem VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | Esta interface fornece suporte à extensão de namespace. | Controle de origem VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | O VSPackage usa essa interface para integrar uma extensão de namespace nas caixas de diálogo **Novo,** **Abrir**ou **Salvar.** Consequentemente, os projetos podem ser automaticamente adicionados ao controle de origem na criação ou adicionados ao controle de origem quando uma operação de salvamento estiver em vigor. | Controle de origem VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | O VSPackage usa esta interface para definir glifos adicionais como glifos de controle de origem para nódulos no **Solution Explorer**. | Controle de origem VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | A **caixa de** diálogo Adicionar para projetos Web usa essa interface. Ele fornece métodos para navegar por um local de controle de origem e para abrir um projeto web adicionado anteriormente no repositório de controle de origem naquele local. | Controle de origem VSPackage | Recomendadas |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | Esta interface fornece suporte para carregamento assíncrono (plano de fundo) de projetos a partir do controle de origem. | Controle de origem VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | Esta interface permite que os projetos observem o <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>progresso do carregamento assíncrono iniciado por . | Project | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | Esta interface permite que o IDE consulta o controle de origem ativo VSPackage. O IDE consulta o valor das configurações de controle de origem que têm significado mesmo quando não há controle de origem ativo VSPackage registrado. Esta interface é implementada [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]e tratada por . | Stub de controle de origem | Obrigatório |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | Esta interface é usada para registrar o controle de origem VSPackage. | Stub de controle de origem | Obrigatório |
| <xref:EnvDTE.SourceControl> | Esta interface é usada em automação. Como tal, ele expõe apenas funções que podem ser executadas sem exibir qualquer ui. | Controle de origem VSPackage | Opcional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | Esta interface é usada para salvar as configurações de controle de origem no arquivo solution (.sln). As configurações incluem o local de controle de origem e os sinalizadores de status de controle de origem. | Controle de origem VSPackage | Recomendadas |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | Esta interface é usada para salvar as configurações de controle de origem no arquivo opções de solução (.suo). Isso pode incluir configurações de controle de origem específicas do usuário, como o local de alistamento do usuário atual. | Controle de origem VSPackage | Recomendadas |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | Essa interface é usada para monitorar eventos para executar operações como verificar arquivos de projeto antes de fechar soluções ou obter novos arquivos do controle de origem ao abrir um projeto. | Controle de origem VSPackage | Recomendadas |

## <a name="see-also"></a>Confira também
- [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)
