---
title: Personalizado (debug interface Access SDK) | Microsoft Docs
description: Encontre informações de referência sobre tipos de símbolo personalizados (identificados com a marca SymTagCustom) no SDK de acesso à interface de depuração do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Custom symbol
ms.assetid: a219fc83-d2a8-4bc5-b7e1-bfafeb247f16
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 322619bbfa759d97061aa3b62ddc65fde43db8e4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857380"
---
# <a name="custom-debug-interface-access-sdk"></a>Custom (SDK de Acesso à Interface de Depuração)
Alguns compiladores apresentam símbolos que não são identificados por nenhum dos tipos de símbolo léxicos padrão. Esses símbolos são identificados por uma `SymTagCustom` marca.

## <a name="properties"></a>Propriedades
 A tabela a seguir mostra as propriedades que são válidas para esse tipo de símbolo.

|Propriedade|Tipo de dados|Descrição|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|`BYTE`|Matriz de dados associada ao símbolo.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID do índice do símbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retorna `SymTagCustom` (um dos valores de [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="see-also"></a>Consulte também
- [Hierarquia lexical de tipos de símbolo](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)