---
title: Implementando um serviço de linguagem legado1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707692"
---
# <a name="implementing-a-legacy-language-service"></a>Implementando um serviço de linguagem herdado
Você pode usar classes no mpf (managed package framework) para implementar um serviço de linguagem legado que suporta uma grande variedade de recursos, como destaque de sintaxe, correspondência de chaves e conclusão do IntelliSense.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova maneira de implementar um serviço de idiomas, consulte [Editor e Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="in-this-section"></a>Nesta seção
- [Visão geral do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-overview.md)

 Uma visão geral dos recursos de serviço de idiomas que são suportados no MPF.

- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Descreve o que é necessário para implementar um serviço de idioma usando o MPF.

- [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Descreve as etapas necessárias para registrar um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]serviço de idioma baseado no MPF com .

- [Analisador e scanner do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Descreve os dois analisadores que são obrigados a implementar todos os recursos de um serviço de idioma usando o MPF.

- [Passo a passo: criando um serviço de linguagem herdado](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Fornece as etapas básicas necessárias para implementar um serviço de idioma MPF em um VSPackage.

- [Passo a passo: obtendo uma lista de snippets de código instalados (implementação herdada)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Demonstra as técnicas de recuperação de uma lista de trechos de código instalados.

- [Recursos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md)

 Fornece links para tópicos que detalham o que deve ser feito para implementar todos os recursos de um serviço de idiomas usando o MPF.
