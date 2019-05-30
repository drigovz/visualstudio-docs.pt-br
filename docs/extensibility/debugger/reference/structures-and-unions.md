---
title: Estruturas e uniões | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2da39e0327f9a0be2cf0f61227de5ea51af03285
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329124"
---
# <a name="structures-and-unions"></a>Estruturas e uniões
A seguir é estruturas e uniões no SDK do Visual Studio de depuração.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Especifica a ID de processo, que pode ser uma ID de sistema ou um GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) descreve as condições sob as quais um ponto de interrupção será acionado.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) descreve a resolução de um ponto de interrupção de erro, incluindo local, o programa e o thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Especifica o tipo de estrutura usada para descrever o local do ponto de interrupção.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) define os componentes que descrevem a localização de um ponto de interrupção em um endereço no código.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) descreve o local de um ponto de interrupção está associado diretamente a um endereço no programa que está sendo depurado.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) descreve o local de um ponto de interrupção na linha em um arquivo de origem do código.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) descreve o local de deslocamento de um ponto de interrupção em uma função no código.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) usada para definir pontos de interrupção de código com base em uma cadeia de caracteres que o usuário pode inserir a partir do IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) usada para definir pontos de interrupção de dados se baseiam em uma cadeia de caracteres que o usuário pode inserir a partir do IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) descreve a resolução de um ponto de interrupção em um local específico.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) descreve a contagem e condições no qual um ponto de interrupção será acionado depois de ter sido passado.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) contém as informações necessárias para implementar um ponto de interrupção.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) contém as informações necessárias para implementar um ponto de interrupção (mesmo que o [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estrutura mas não inclui informações de GUID, restrição e tracepoint do fornecedor).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) descreve o local de um ponto de interrupção de código.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) descreve o resultado da associação a um ponto de interrupção de dados.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) descreve as informações de ponto de interrupção associada para um ponto de interrupção de código ou um ponto de interrupção de dados.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Especifica a estrutura do local de resolução de ponto de interrupção.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) descreve uma matriz de cadeias de caracteres.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Especifica informações sobre um tipo de campo tirado de metadados.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) descreve uma chamada para uma função ou método.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) descreve o computador no qual o depurador está em execução.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) descreve uma lista de GUIDs.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) descreve um contexto de memória ou o contexto de código.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) descreve um endereço em um programa que está sendo depurado.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) representa um dos vários tipos diferentes de endereços.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) identifica um visualizador personalizado ou o Visualizador de tipo.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) descreve uma propriedade de depuração que por sua vez descreve um objeto de uma natureza hierárquica que tem o nome, tipo e valor.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) descreve uma referência.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) descreve desmontagem ao IDE para exibição.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) descreve um erro de tempo de execução ou a exceção lançado pelo programa que está sendo depurado.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) descreve uma variável local, parâmetro ou outro campo.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) descreve um quadro de pilha.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) descreve uma matriz de identificadores exclusivos para mecanismos de depuração disponíveis.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) usado para definir as informações de JustMyCode para um módulo.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) descreve uma determinada máquina.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) descreve um elemento de matriz em uma matriz.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) descreve o endereço de um campo de uma classe ou estrutura.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) descreve o endereço de uma variável local dentro de um escopo (geralmente uma função ou método).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) descreve o endereço de um método de uma classe.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) descreve um parâmetro de um método ou função.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) descreve um valor de retorno de um método ou função.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) descreve um tipo de campo tirado de metadados.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) descreve um módulo específico (DLL, EXE ou assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) descreve informações de status sobre caminhos de pesquisa de símbolo que foram pesquisados.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) descreve um endereço nativo.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) descreve um tipo de campo extraído de um símbolo PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) descreve o estado de um ponto de interrupção que está pronto para associar a um local de código.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) descreve um processo.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) descreve uma lista de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos que representam nós de programa.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) descreve processos em execução em um computador.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) descreve o local de linha e coluna em que o texto especificado.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) descreve as propriedades de um thread.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) descreve um tipo de campo.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) descreve um endereço físico.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) descreve um endereço que é relativo a um `this` ponteiro (`Me` no Visual Basic).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h, sh.h ou ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Referência de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)