---
title: erros de FxCopCmd
ms.date: 10/19/2016
description: Saiba mais sobre os códigos de erro que o comando FxCopCmd retorna. Veja qual tipo de erro cada código representa e descubra como reconhecer erros fatais.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: efeabd85bbf2753dd3f5e37a43e0918b7f95d7fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860211"
---
# <a name="fxcopcmd-tool-errors"></a>Erros da ferramenta FxCopCmd

FxCopCmd não considera que todos os erros sejam fatais. Se FxCopCmd tiver informações suficientes para executar uma análise parcial, ele executará os erros de análise e relatórios que ocorreram. O código de erro, que é um número inteiro de 32 bits, contém uma combinação bit a bit de valores numéricos que correspondem a erros.

A tabela a seguir descreve os códigos de erro retornados por FxCopCmd:

|Erro|Valor numérico|
|-----------|-------------------|
|Nenhum erro|0x0|
|Erro de análise|0x1|
|Exceções da regra|0x2|
|Erro de carregamento do projeto|0x4|
|Erro de carregamento do assembly|0x8|
|Erro de carregamento da biblioteca de regras|0x10|
|Erro ao carregar o relatório de importação|0x20|
|Erro de saída|0x40|
|Erro de opção de linha de comando|0x80|
|Erro de inicialização|0x100|
|Erro de referências de assembly|0x200|
|BuildBreakingMessage|0x400|
|Erro desconhecido|0x1000000|

O **erro de análise** é retornado para erros fatais. Isso indica que a análise não pôde ser concluída. Quando aplicável, o código de erro também contém a causa subjacente do erro fatal. As seguintes condições geram erros fatais:

- Não foi possível executar a análise devido à insuficiência de entrada.

- A análise gerou uma exceção que não é tratada pelo FxCopCmd.

- O arquivo de projeto especificado não pôde ser encontrado ou está corrompido.

- A opção de saída não foi especificada ou o arquivo não pôde ser gravado.

> [!NOTE]
> O assembly de código de retorno FxCopCmd **referencia o erro** 0x200 por si só é um aviso em vez de um erro. Esse código de retorno indica que há referências indiretas ausentes, mas que FxCopCmd foi capaz de tratá-las. O aviso significa que há uma possibilidade de que alguns resultados da análise possam ter sido comprometidos. Tratar **erro de referências de assembly** como um erro quando ele é combinado com qualquer outro código de retorno.

## <a name="see-also"></a>Confira também

- [Erros do aplicativo de análise do código](../code-quality/code-analysis-application-errors.md)
