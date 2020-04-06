---
title: Consulta Editar editar query Save (Controle de origem VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705967"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Editar e salvar consulta (VSPackage de controle do código-fonte)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]os editores podem transmitir eventos de Query Edit Query Save (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]O Source Control Stub implementa o serviço QEQS, de modo que ele seja o destinatário de eventos QEQS. Esses eventos são então delegados para o controle de origem ativo VSPackage. O controle de origem ativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> VSPackage implementa os métodos. Os métodos `IVsQueryEditQuerySave2` da interface são normalmente chamados imediatamente antes de um documento ser editado pela primeira vez e imediatamente antes de um documento ser salvo.

## <a name="queryeditquerysave-events"></a>ConsultaEditQuerySalvar eventos
 O controle de origem VSPackage deve lidar com `IVsQueryEditQuerySave2` os eventos QEQS implementando a interface e os métodos necessários. Abaixo está uma breve descrição dos dois métodos que o VSPackage deve implementar no mínimo. A implementação real deve estar de acordo com a lógica do modelo de controle de origem.

### <a name="queryeditfiles-method"></a>Método queryEditFiles
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> é chamado quando qualquer projeto ou editor quer modificar um arquivo. Idealmente, este método é chamado *antes* do arquivo ser modificado e quando um arquivo é salvo. Quando invocado, `IVsQueryEditQuerySave2::QueryEditFiles` o método verifica se os arquivos dado estão sob controle de origem, se eles precisam ser verificados e se eles podem ser recarregados. Se as circunstâncias impedirem que `IVsQueryEditQuerySave2::QueryEditFiles` os arquivos sejam editáveis, o método diz ao programa de chamada para cancelar a edição. Também é possível que o chamador especifique um modo de invocação. No modo "silencioso", este método só entra em ação se não fizer com que nenhuma ui apareça. Se a ui for inevitável, uma bandeira deve ser devolvida para indicar o problema.

 O método se comporta de forma transacional; ou seja, se a edição for cancelada em um único arquivo, a edição será cancelada para todos os arquivos. Por outro lado, se a edição for permitida, é permitido para todos os arquivos. Se este método permitir a edição uma vez para um determinado conjunto de arquivos, ele deve sempre permitir a edição em chamadas subseqüentes para o mesmo conjunto de arquivos. O loop de edição de permitir continua até que os arquivos sejam fechados, salvos e recarregados; até que seus atributos (propriedades) mudem; ou até que o pacote de controle de origem seja alterado. Os casos a considerar `IVsQueryEditQuerySave2::QueryEditFiles` na implementação do método incluem vários arquivos, arquivos especiais, cancelamento de edições do usuário e na memória.

### <a name="querysavefiles-method"></a>Método De consultaSaveFiles
 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> é chamado quando qualquer projeto ou editor precisa salvar um conjunto de arquivos. Quando invocado, `IVsQueryEditQuerySave2::QuerySaveFiles` o método verifica se os arquivos dado são somente leitura e se estão sob controle de origem. Se os arquivos precisarem ser verificados, a chamada é delegada para o pacote de controle de origem. Se as circunstâncias impedirem que `IVsQueryEditQuerySave2::QuerySaveFiles` os arquivos sejam salvos, o método deve dizer ao editor para cancelar o save. Assim como `IVsQueryEditQuerySave2::QueryEditFiles` no método, é possível que o chamador especifique um modo de invocação. No modo "silencioso", este método só entra em ação se não fizer com que nenhuma ui apareça. Se a ui for inevitável, uma bandeira deve ser devolvida para indicar o problema.

 Este método deve comportar-se de forma transacional; ou seja, se o save for cancelado em um único arquivo, o save será cancelado para todos os arquivos. Por outro lado, se a salvação for permitida, deve ser permitida para todos os arquivos. Assim como `IVsQueryEditQuerySave2::QueryEditFiles` no método, os casos `IVsQueryEditQuerySave2::QuerySaveFiles` a considerar na implementação do método incluem vários arquivos, arquivos especiais, cancelamento do usuário e edições na memória.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
