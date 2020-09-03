---
title: Segurança dos modelos de texto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24a90d4e7af351fc4ba5807d2af7830edede9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671224"
---
# <a name="security-of-text-templates"></a>Segurança de modelos de texto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os modelos de texto têm as seguintes preocupações de segurança:

- Os modelos de texto são vulneráveis a inserções de código arbitrárias.

- Se o mecanismo que o host usa para localizar um processador de diretiva não for seguro, um processador de diretiva mal-intencionada poderá ser executado.

## <a name="arbitrary-code"></a>Código arbitrário
 Ao escrever um modelo, você pode colocar qualquer código dentro das \<# #> marcas. Isso permite que um código arbitrário seja executado de dentro de um modelo de texto.

 Certifique-se de obter modelos de fontes confiáveis. Certifique-se de avisar os usuários finais do seu aplicativo para não executar modelos que não venham de fontes confiáveis.

## <a name="malicious-directive-processor"></a>Processador de diretiva mal-intencionado
 O mecanismo de modelo de texto interage com um host de transformação e um ou mais processadores de diretiva para transformar o texto do modelo em um arquivo de saída. Para obter mais informações, consulte [o processo de transformação do modelo de texto](../modeling/the-text-template-transformation-process.md).

 Se o mecanismo que o host usa para encontrar um processador de diretiva não é seguro, ele corre o risco de executar um processador de diretiva mal-intencionado. O processador de diretiva mal-intencionado pode fornecer um código que é executado no `FullTrust` modo quando o modelo é executado. Se você criar um host de transformação de modelo de texto personalizado, deverá usar um mecanismo seguro, como o registro, para que o mecanismo Localize os processadores de diretiva.
