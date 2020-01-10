---
title: Segurança de modelos de texto
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25815bcb7f027501fb849dcd29d14b040c24d7fa
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591964"
---
# <a name="security-of-text-templates"></a>Segurança de modelos de texto
Os modelos de texto têm as seguintes preocupações de segurança:

- Os modelos de texto são vulneráveis a inserções de código arbitrárias.

- Se o mecanismo que o host usa para localizar um processador de diretiva não for seguro, um processador de diretiva mal-intencionada poderá ser executado.

## <a name="arbitrary-code"></a>Código arbitrário
 Ao escrever um modelo, você pode colocar qualquer código dentro das marcas \<# # >. Isso permite que um código arbitrário seja executado de dentro de um modelo de texto.

 Certifique-se de obter modelos de fontes confiáveis. Certifique-se de avisar os usuários finais do seu aplicativo para não executar modelos que não venham de fontes confiáveis.

## <a name="malicious-directive-processor"></a>Processador de diretiva mal-intencionado
 O mecanismo de modelo de texto interage com um host de transformação e um ou mais processadores de diretiva para transformar o texto do modelo em um arquivo de saída. Para obter mais informações, consulte [o processo de transformação do modelo de texto](../modeling/the-text-template-transformation-process.md).

 Se o mecanismo que o host usa para encontrar um processador de diretiva não é seguro, ele corre o risco de executar um processador de diretiva mal-intencionado. O processador de diretivas mal-intencionadas pode fornecer um código que é executado no modo de `FullTrust` quando o modelo é executado. Se você criar um host de transformação de modelo de texto personalizado, deverá usar um mecanismo seguro, como o registro, para que o mecanismo Localize os processadores de diretiva.
