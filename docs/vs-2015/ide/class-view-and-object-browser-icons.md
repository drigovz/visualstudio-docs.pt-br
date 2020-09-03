---
title: Ícones de Modo de Exibição de Classe e Pesquisador de Objetos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e67763234ff7b3778cccabaed45fbbc0bc04d30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620479"
---
# <a name="class-view-and-object-browser-icons"></a>Exibição de classe ícones do Pesquisador de Objetos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Modo de Exibição de Classe** e o **Pesquisador de Objetos** exibem ícones que representam entidades de código, por exemplo, namespaces, classes, funções e variáveis. A tabela a seguir ilustra e descreve os ícones.

|ícone|Descrição|ícone|Descrição|
|----------|-----------------|----------|-----------------|
|![Símbolo de namespace](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Namespace|![Símbolo de declaração](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Método ou função|
|![Ícone de classe](../ide/media/vxclass-icon.gif "vxClass_Icon")|Classe|![Símbolo de operador](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|Operador|
|![Símbolo de interface pirulito](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Interface|![Símbolo de propriedade](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Propriedade|
|![Símbolo de estrutura](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Estrutura|![Ícone de campo](../ide/media/vxfield-icon.gif "vxField_Icon")|Campo ou variável|
|![Símbolo de união](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Union|![Símbolo de evento](../ide/media/vxevent-icon.gif "vxEvent_Icon")|Evento|
|![Símbolo de enumeração](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enumeração|![Ícone constante](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Constante|
|![Símbolo de definição de tipo](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Símbolo do item de enumeração](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Item Enum|
|![Símbolo do módulo do Visual Studio](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Módulo|![Símbolo do item de mapa](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Item de Mapa|
|![Símbolo do método de extensão](../ide/media/extensionmethod.gif "ExtensionMethod")|Método de extensão|![Símbolo de declaração](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Declaração externa|
|![Símbolo de delegado](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|Delegar|![Ícone de erro para Modo de Exibição de Classe e Pesquisador de Objetos](../ide/media/erroricon.gif "ErrorIcon")|Erro|
|![Símbolo de exceção](../ide/media/vxexception-icon.gif "vxException_Icon")|Exceção|![Símbolo de modelo](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Modelo|
|![Símbolo de mapa](../ide/media/vxmap-icon.gif "vxMap_Icon")|Mapa|![Símbolo de ponto de exclamação de erro](../ide/media/vxerror-icon.gif "vxError_Icon")|Desconhecido|
|![Símbolo de encaminhamento de tipo](../ide/media/ob-type-forward.gif "ob_type_forward")|Encaminhamento de tipo|||

## <a name="signal-icons"></a>Ícones de sinal
 Os ícones de sinal a seguir aplicam-se a todos os ícones anteriores e indicam sua acessibilidade.

> [!NOTE]
> Se seu projeto estiver incluído em um banco de dados de controle do código-fonte, ícones de sinal adicionais poderão ser exibidos para indicar o status de controle de origem, como check-in ou check-out.

|ícone|Descrição|
|----------|-----------------|
|\<No Signal Icon>|Público. Acessível de qualquer lugar neste componente e de qualquer componente que faça referência a ele.|
|![Símbolo protegido por sinal](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Protegido. Acessível da classe ou do tipo recipiente ou daqueles derivados da classe ou do tipo recipiente.|
|![Símbolo privado de sinal](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Privado. Acessível somente na classe ou no tipo recipiente.|
|![Símbolo selado por sinal](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Lacrado.|
|![Sinalizar amigo&#47;símbolo interno](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Amigo/interno. Acessível somente no projeto.|
|![Seta do ícone de sinal](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Atalho. Um atalho para o objeto.|

## <a name="see-also"></a>Consulte Também
 [Exibindo a estrutura do código](../ide/viewing-the-structure-of-code.md)
