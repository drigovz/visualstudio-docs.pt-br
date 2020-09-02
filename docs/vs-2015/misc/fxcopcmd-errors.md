---
title: Erros de FxCopCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787281"
---
# <a name="fxcopcmd-errors"></a>Erros (FxCopCmd)
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
  
 O erro de análise é retornado para erros fatais. Isso indica que a análise não pôde ser concluída. Quando aplicável, o código de erro também contém a causa subjacente do erro fatal. As seguintes condições geram erros fatais:  
  
- Não foi possível executar a análise causada por entrada insuficiente.  
  
- A análise gerou uma exceção que não é tratada pelo FxCopCmd.  
  
- O arquivo de projeto especificado não pôde ser encontrado ou está corrompido.  
  
- A opção de saída não foi especificada ou o arquivo não pôde ser gravado.  
  
    > [!NOTE]
    > O código de retorno do FxCopCmd "erro de referências de assembly" 0x200 por si só é um aviso em vez de um erro. Esse código de retorno indica que foram encontradas referências indiretas ausentes, mas que FxCopCmd foi capaz de tratá-las. É um aviso de que há uma possibilidade de que alguns resultados da análise possam ter sido comprometidos. Considere o código de retorno de "erro de referências de assembly" como um erro quando ele é combinado com qualquer outro código de retorno.  
  
## <a name="see-also"></a>Consulte Também  
 [Erros do aplicativo de análise do código](../code-quality/code-analysis-application-errors.md)