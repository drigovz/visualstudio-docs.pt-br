---
title: Consulta editar consulta salvar (controle do código-fonte VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be12297bdaeb112d7421b02da1153ed62d6d14f8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724766"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Editar e salvar consulta (VSPackage de controle do código-fonte)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editores podem difundir eventos de salvamento de consulta de edição de consulta (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stub de controle do código-fonte implementa o serviço QEQS, para que ele seja o destinatário de eventos de QEQS. Esses eventos são então delegados para o VSPackage de controle do código-fonte ativo no momento. O VSPackage de controle do código-fonte ativo implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e seus métodos. Os métodos da interface de `IVsQueryEditQuerySave2` geralmente são chamados imediatamente antes de um documento ser editado pela primeira vez e imediatamente antes de um documento ser salvo.

## <a name="queryeditquerysave-events"></a>Eventos de QueryEditQuerySave
 O VSPackage de controle do código-fonte deve manipular os eventos de QEQS implementando a interface `IVsQueryEditQuerySave2` e os métodos necessários. Veja abaixo uma breve descrição dos dois métodos que o VSPackage deve implementar no mínimo. A implementação real deve estar de acordo com a lógica do modelo de controle do código-fonte.

### <a name="queryeditfiles-method"></a>Método QueryEditFiles
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> é chamado quando qualquer projeto ou editor deseja modificar um arquivo. O ideal é que esse método seja chamado *antes* de o arquivo ser modificado e quando um arquivo é salvo. Quando invocado, o método `IVsQueryEditQuerySave2::QueryEditFiles` verifica se os arquivos fornecidos estão sob controle do código-fonte, se eles precisam ser extraídos e se podem ser recarregados. Se as circunstâncias impedirem que os arquivos sejam editáveis, o método `IVsQueryEditQuerySave2::QueryEditFiles` instruirá o programa de chamada a cancelar a edição. Também é possível que o chamador especifique um modo de invocação. No modo "silencioso", esse método executará uma ação somente se não fizer com que nenhuma interface do usuário apareça. Se a interface do usuário for inevitável, um sinalizador deverá ser retornado para indicar o problema.

 O método se comporta de forma transacional; ou seja, se a edição for cancelada em um único arquivo, a edição será cancelada para todos os arquivos. Por outro lado, se a edição for permitida, ela será permitida para todos os arquivos. Se esse método permitir a edição uma vez para um determinado conjunto de arquivos, ele deverá sempre permitir a edição nas chamadas subsequentes para o mesmo conjunto de arquivos. O loop Allow-Edit continua até que os arquivos sejam fechados, salvos e recarregados; até que seus atributos (Propriedades) mudem; ou até que o pacote de controle do código-fonte seja alterado. Os casos a serem considerados na implementação do método `IVsQueryEditQuerySave2::QueryEditFiles` incluem vários arquivos, arquivos especiais, cancelamento do usuário e edições na memória.

### <a name="querysavefiles-method"></a>Método QuerySaveFiles
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> é chamado quando qualquer projeto ou editor precisa salvar um conjunto de arquivos. Quando invocado, o método `IVsQueryEditQuerySave2::QuerySaveFiles` verifica se os arquivos fornecidos são somente leitura e se estão sob controle do código-fonte. Se for necessário fazer check-out dos arquivos, a chamada será delegada ao pacote de controle do código-fonte. Se as circunstâncias impedirem que os arquivos sejam salvos, o método `IVsQueryEditQuerySave2::QuerySaveFiles` deverá informar ao editor para cancelar o salvamento. Assim como com o método `IVsQueryEditQuerySave2::QueryEditFiles`, é possível que o chamador especifique um modo de invocação. No modo "silencioso", esse método executará uma ação somente se não fizer com que nenhuma interface do usuário apareça. Se a interface do usuário for inevitável, um sinalizador deverá ser retornado para indicar o problema.

 Esse método deve se comportar de forma transacional; ou seja, se o salvamento for cancelado em um único arquivo, o salvamento será cancelado para todos os arquivos. Por outro lado, se o salvamento for permitido, ele deverá ser permitido para todos os arquivos. Assim como acontece com o método `IVsQueryEditQuerySave2::QueryEditFiles`, os casos a serem considerados na implementação do método `IVsQueryEditQuerySave2::QuerySaveFiles` incluem vários arquivos, arquivos especiais, cancelar do usuário e edições na memória.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>