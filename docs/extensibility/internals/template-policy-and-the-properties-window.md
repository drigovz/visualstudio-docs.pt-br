---
title: Política de modelo e a janela Propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7135a7c99f1566eaacb4079e9787cf2b5606682
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722685"
---
# <a name="template-policy-and-the-properties-window"></a>Política de modelo e a janela Propriedades
Quando um projeto está contido dentro de um projeto de modelo empresarial, esse projeto de modelo empresarial pode impor a política. A política de modelo se torna um sistema restrito que pode ser usado para definir valores padrão para propriedades, ocultar propriedades, adicionar propriedades e assim por diante.

 O uso da política de modelo para controlar a exibição de informações na janela **Propriedades** é diferente da implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> manipula as propriedades do objeto no nível do componente, enquanto a diretiva de modelo pode ser usada para restringir as propriedades do objeto no nível da solução ou do projeto. Em outras palavras

- Implementar os métodos em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> para determinar o que é exibido na janela **Propriedades** para objetos específicos

- Usar a política de modelo no nível da solução e do projeto para determinar o que é exibido na janela **Propriedades** de objetos especificados anteriormente

  Usar a política de modelo para restringir seletivamente propriedades específicas na janela **Propriedades** quando um item de projeto de um tipo especificado é selecionado em **Gerenciador de soluções** pode ser benéfico para todos os membros da equipe de desenvolvimento que trabalham em um projeto. Por exemplo, usando a política de modelo, você pode configurar todas as informações de cadeia de conexão em um banco de dados para seus desenvolvedores e tornar a cadeia de conexão somente leitura. Dessa forma, você pode fornecer uma maneira simples de garantir que cada desenvolvedor Use o caminho correto para acesso a dados.

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Estender as propriedades](../../extensibility/internals/extending-properties.md)