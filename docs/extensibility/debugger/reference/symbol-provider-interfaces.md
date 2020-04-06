---
title: Interfaces do provedor de símbolos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7929ba36c76f0db1cabab087afe3590de509efff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715844"
---
# <a name="symbol-provider-interfaces"></a>Interfaces de provedor de símbolos
A seguir estão as Interfaces [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]de manuseio de símbolos para o .

## <a name="discussion"></a>Discussão
 Essas interfaces são usadas para avaliar variáveis em uma pilha de chamadas durante o modo de pausa. Eles são implementados apenas para provedores de símbolos de tempo de execução de idiomas comuns (SP).

|Interface|Implementado por|Descrição|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Representa o endereço de um item.|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|Representa o endereço de um item, fornecendo acesso ao ID do processo.|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Representa um símbolo de matriz ou tipo de matriz.|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Representa um símbolo de classe ou tipo de classe.|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Representa um provedor de símbolos COM+ com métodos específicos para código gerenciado.|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Representa um provedor de símbolos COM+ com métodos específicos para código gerenciado e estende o **IDebugComPlusSymbolProvider**.|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Representa um símbolo ou tipo que é um recipiente para outros símbolos ou tipos.|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Representa um atributo personalizado que pode ser anexado a um símbolo.|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Representa uma consulta para atributos personalizados em um método ou tipo.|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Fornece acesso a atributos personalizados em um símbolo.|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|A interface base para qualquer tipo que possa ser determinada em tempo de execução.|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Representa um campo dinâmico para um objeto [IDebugBinder.](../../../extensibility/debugger/reference/idebugbinder.md)|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Representa um tipo de enumeração.|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|Amplia os tipos de campos disponíveis para suportar genéricos de código gerenciados.|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|A classe base para todos os campos; representa uma descrição de um símbolo ou tipo.|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Representa a definição de um campo para um tipo genérico de código gerenciado.|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Representa uma instância de um campo para um tipo genérico de código gerenciado.|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Representa um parâmetro para um tipo genérico de código gerenciado.|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Representa um método.|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Representa um modificador opcional de depuração.|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Representa um ponteiro.|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Representa um valor de enumeração do tipo primitivo a partir de uma interface [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Representa uma propriedade de uma classe de código gerenciada que pode ser get ou set.|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Representa um provedor de símbolos que fornece símbolos e tipos.|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Representa um provedor de símbolos com acesso direto a metadados e interfaces de símbolos principais.|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Representa a capacidade de criar um campo que representa um tipo.|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Estende o **IDebugTypeFieldBuilder** para poder criar tipos de array.|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Representa uma coleção de objetos [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Representa uma coleção de objetos [IDebugCustomAttribute.](../../../extensibility/debugger/reference/idebugcustomattribute.md)|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Representa uma coleção de objetos [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)|

## <a name="see-also"></a>Confira também
- [Referência da API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
