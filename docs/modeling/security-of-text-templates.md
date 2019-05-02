---
title: Segurança de modelos de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66159516c6b1360203130dedb56c0e6c192a118a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824014"
---
# <a name="security-of-text-templates"></a>Segurança de modelos de texto
Modelos de texto têm as seguintes preocupações de segurança:

- Modelos de texto são vulneráveis a inserções de código arbitrário.

- Se o mecanismo que o host usa para encontrar um processador de diretriz não é seguro, um processador de diretriz mal-intencionado pode ser executado.

## <a name="arbitrary-code"></a>Código arbitrário
 Quando você escreve um modelo, você pode colocar qualquer código dentro de \<# # > marcas. Isso permite que o código arbitrário ser executado em um modelo de texto.

 Certifique-se de que obter modelos de fontes confiáveis. Certifique-se avisar os usuários finais do seu aplicativo para não executar modelos que não vêm de fontes confiáveis.

## <a name="malicious-directive-processor"></a>Processador de diretriz mal-intencionados
 O mecanismo de modelo de texto interage com um host de transformação e um ou mais processadores de diretriz para transformar o texto do modelo para um arquivo de saída. Para obter mais informações, consulte [o processo de transformação de modelo de texto](../modeling/the-text-template-transformation-process.md).

 Se o mecanismo que o host usa para encontrar um processador de diretriz não é seguro, ele corre o risco da execução de um processador de diretriz mal-intencionado. O processador de diretriz mal-intencionado poderia fornecer código que é executado em `FullTrust` modo quando o modelo é executado. Se você criar um host de transformação do modelo de texto personalizado, você deve usar um mecanismo seguro, como o registro, para o mecanismo localizar os processadores de diretriz.