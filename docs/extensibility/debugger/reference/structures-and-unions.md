---
title: Estruturas e Sindicatos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19d8f547d98488edffc6049be7619e5b5e921d93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713488"
---
# <a name="structures-and-unions"></a>Estruturas e uniões
A seguir estão estruturas e sindicatos no Visual Studio Debugging SDK.

- [AD_PROCESS_ID AD_PROCESS_ID.](../../../extensibility/debugger/reference/ad-process-id.md) Especifica o ID do processo, que pode ser um ID do sistema ou um GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Descreve as condições sob as quais um ponto de ruptura disparará.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Descreve a resolução de um ponto de ruptura de erro, incluindo localização, programa e segmento.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Especifica o tipo de estrutura usada para descrever a localização do ponto de ruptura.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Define os componentes que descrevem a localização de um ponto de ruptura em um endereço em código.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Descreve a localização de um ponto de ruptura que está vinculado diretamente a um endereço no programa que está sendo depurado.

- [BP_LOCATION_CODE_FILE_LINE BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Descreve a localização de um ponto de ruptura na linha em um arquivo fonte de código.

- [BP_LOCATION_CODE_FUNC_OFFSET BP_LOCATION_CODE_FUNC_OFFSET.](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Descreve a localização de deslocamento de um ponto de ruptura em uma função em código.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Usado para definir pontos de interrupção de código com base em uma seqüência que o usuário pode inserir a partir do IDE.

- [BP_LOCATION_DATA_STRING.](../../../extensibility/debugger/reference/bp-location-data-string.md) Usado para definir pontos de interrupção de dados que são baseados em uma seqüência que o usuário pode inserir a partir do IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Descreve a resolução de um ponto de ruptura em um local específico.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Descreve a contagem e as condições sobre as quais um ponto de ruptura será disparado depois de ter sido previamente passado.

- [BP_REQUEST_INFO.](../../../extensibility/debugger/reference/bp-request-info.md) Contém as informações necessárias para implementar um ponto de ruptura.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Contém as informações necessárias para implementar um ponto de ruptura (o mesmo que a estrutura [BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) mas inclui informações de GUIA, restrição e tracepoint do fornecedor).

- [BP_RESOLUTION_CODE BP_RESOLUTION_CODE.](../../../extensibility/debugger/reference/bp-resolution-code.md) Descreve a localização de um ponto de quebra de código.

- [BP_RESOLUTION_DATA BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Descreve o resultado da vinculação de um ponto de ruptura de dados.

- [BP_RESOLUTION_INFO BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Descreve as informações de ponto de ruptura vinculados para um ponto de ruptura de código ou um ponto de ruptura de dados.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Especifica a estrutura do local de resolução do ponto de ruptura.

- [BSTR_ARRAY BSTR_ARRAY.](../../../extensibility/debugger/reference/bstr-array.md) Descreve uma matriz de strings.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Especifica informações sobre um tipo de campo retirados de metadados.

- [CODE_PATH CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Descreve uma chamada para uma função ou método.

- [COMPUTER_INFO COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Descreve o computador no qual o depurador está sendo executado.

- [CONST_GUID_ARRAY CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Descreve uma lista de GUIDs.

- [CONTEXT_INFO.](../../../extensibility/debugger/reference/context-info.md) Descreve um contexto de memória ou contexto de código.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Descreve um endereço em um programa que está sendo depurado.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Representa um dos vários tipos diferentes de endereços.

- [DEBUG_CUSTOM_VIEWER.](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identifica um visualizador personalizado ou um visualizador de tipo.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Descreve uma propriedade de depuração que, por sua vez, descreve um objeto de natureza hierárquica que tem nome, tipo e valor.

- [DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md) Descreve uma referência.

- [Desmontagem de dados](../../../extensibility/debugger/reference/disassemblydata.md) Descreve a desmontagem ao IDE para exibição.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Descreve uma exceção ou erro de tempo de execução lançado pelo programa que está sendo depurado.

- [FIELD_INFO FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md) Descreve uma variável local, parâmetro ou outro campo.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Descreve um quadro de pilha.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Descreve uma matriz de identificadores exclusivos para motores de depuração disponíveis.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Usado para definir as informações do JustMyCode para um módulo.

- [MACHINE_INFO MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Descreve uma máquina em particular.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Descreve um elemento de matriz dentro de uma matriz.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Descreve o endereço de um campo de classe ou estrutura.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Descreve o endereço de uma variável local dentro de um escopo (geralmente uma função ou método).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Descreve o endereço de um método de uma classe.

- [METADATA_ADDRESS_PARAM METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Descreve um parâmetro de um método ou função.

- [METADATA_ADDRESS_RETVAL METADATA_ADDRESS_RETVAL.](../../../extensibility/debugger/reference/metadata-address-retval.md) Descreve um valor de retorno de um método ou função.

- [METADATA_TYPE METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Descreve um tipo de campo retirado de metadados.

- [MODULE_INFO MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Descreve um módulo específico (DLL, EXE ou montagem).

- [MODULE_SYMBOL_SEARCH_INFO MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Descreve informações de status sobre caminhos de pesquisa de símbolos que foram pesquisados.

- [NATIVE_ADDRESS NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Descreve um endereço nativo.

- [PDB_TYPE PDB_TYPE.](../../../extensibility/debugger/reference/pdb-type.md) Descreve um tipo de campo retirado de um símbolo PDB.

- [PENDING_BP_STATE_INFO.](../../../extensibility/debugger/reference/pending-bp-state-info.md) Descreve o estado de um ponto de ruptura que está pronto para se ligar a um local de código.

- [PROCESS_INFO PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Descreve um processo.

- [PROGRAM_NODE_ARRAY.](../../../extensibility/debugger/reference/program-node-array.md) Descreve uma lista de objetos [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representam os nós do programa.

- [PROVIDER_PROCESS_DATA PROVIDER_PROCESS_DATA.](../../../extensibility/debugger/reference/provider-process-data.md) Descreve processos em execução em uma máquina.

- [TEXT_POSITION TEXT_POSITION.](../../../extensibility/debugger/reference/text-position.md) Descreve a localização da linha e da coluna no texto dado.

- [PROPRIEDADES DE ROSCA](../../../extensibility/debugger/reference/threadproperties.md) Descreve as propriedades de um fio.

- [TYPE_INFO.](../../../extensibility/debugger/reference/type-info.md) Descreve o tipo de campo.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Descreve um endereço físico.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Descreve um endereço relativo `this` a`Me` um ponteiro (no Visual Basic).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h, sh.h, ou ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
