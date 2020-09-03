---
title: Política de modelo e a janela Propriedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c67150c5a71a3d70df85669319795a405c60f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156016"
---
# <a name="template-policy-and-the-properties-window"></a>Política de modelo e a janela Propriedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando um projeto está contido dentro de um projeto de modelo empresarial, esse projeto de modelo empresarial pode impor a política. A política de modelo se torna um sistema restrito que pode ser usado para definir valores padrão para propriedades, ocultar propriedades, adicionar propriedades e assim por diante.  
  
 O uso da política de modelo para controlar a exibição de informações na janela **Propriedades** é diferente da implementação <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> manipula Propriedades de objeto no nível de componente, enquanto a diretiva de modelo pode ser usada para restringir as propriedades de objeto no nível da solução ou do projeto. Em outras palavras  
  
- Implementar os métodos em <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> para determinar o que é exibido na janela **Propriedades** para objetos específicos  
  
- Usar a política de modelo no nível da solução e do projeto para determinar o que é exibido na janela **Propriedades** de objetos especificados anteriormente  
  
  Usar a política de modelo para restringir seletivamente propriedades específicas na janela **Propriedades** quando um item de projeto de um tipo especificado é selecionado em **Gerenciador de soluções** pode ser benéfico para todos os membros da equipe de desenvolvimento que trabalham em um projeto. Por exemplo, usando a política de modelo, você pode configurar todas as informações de cadeia de conexão em um banco de dados para seus desenvolvedores e tornar a cadeia de conexão somente leitura. Dessa forma, você pode fornecer uma maneira simples de garantir que cada desenvolvedor Use o caminho correto para acesso a dados.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
