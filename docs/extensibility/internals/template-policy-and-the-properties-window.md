---
title: Política de modelo e a janela propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704659"
---
# <a name="template-policy-and-the-properties-window"></a>Política de modelo e a janela Propriedades
Quando um projeto está contido dentro de um projeto de modelo corporativo, esse projeto de modelo corporativo pode impor a política. A diretiva de modelo torna-se um sistema de restrição que pode ser usado para definir valores padrão para propriedades, ocultar propriedades, adicionar propriedades e assim por diante.

 O uso da diretiva de modelo **Properties** para controlar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>exibição de informações na janela Propriedades é diferente de implementar . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>lida com propriedades de objeto no nível do componente, enquanto a diretiva de modelo pode ser usada para restringir propriedades de objeto no nível de solução ou projeto. Em outras palavras

- Implemente os <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> métodos para determinar o que é exibido na janela **Propriedades** para objetos específicos

- Use a diretiva de modelo na solução e no nível do projeto para determinar o que é exibido na janela **Propriedades** para objetos especificados anteriormente

  Usar a diretiva de modelo para restringir seletivamente propriedades específicas na janela **Propriedades** quando um item de projeto de um tipo especificado é selecionado no **Solution Explorer** pode ser benéfico para todos os membros da equipe de desenvolvimento que trabalham em um projeto. Por exemplo, usando a diretiva de modelo, você pode configurar todas as informações de seqüência de conexões em um banco de dados para seus desenvolvedores e tornar a seqüência de conexões somente leitura. Dessa forma, você pode fornecer uma maneira simples de garantir que cada desenvolvedor use o caminho correto para o acesso aos dados.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
