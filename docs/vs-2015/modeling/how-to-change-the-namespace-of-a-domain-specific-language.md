---
title: 'Como: Alterar o Namespace de uma linguagem específica de domínio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, namespace
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 57ec75ec116b3b107b01a139621d3c59ca8ecac9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094898"
---
# <a name="how-to-change-the-namespace-of-a-domain-specific-language"></a>Como: Alterar o namespace de uma Linguagem Específica de Domínio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode alterar o namespace de uma linguagem específica de domínio. Você deve fazer a alteração no valor de **Gerenciador de DSL**, nas propriedades do projeto Dsl de pacote e as informações de assembly.  
  
### <a name="to-change-the-namespace-of-a-domain-specific-language"></a>Para alterar o namespace de uma linguagem específica de domínio  
  
1. Na **Gerenciador de DSL**, clique no **Dsl** nó.  
  
2. No **propriedades** janela, altere o **Namespace** propriedade.  
  
3. Salve a solução e transformar os modelos.  
  
4. Sobre o **Project** menu, clique em **Dsl propriedades**.  
  
     As propriedades do projeto são exibidos.  
  
5. Clique na guia **Aplicativo**.  
  
6. Alterar o **namespace padrão** propriedade para o novo nome de namespace.  
  
7. Se você também quiser alterar o nome do assembly, altere o **propriedade nome do Assembly.**  
  
8. Se você tiver alterado o nome do Assembly, abra DslPackage\Package.tt e atualize essa linha:  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. Se você tiver gravado um código personalizado, certifique-se de alterar as referências de namespace e classe nos arquivos de código.  
  
10. Redefina a instância Experimental do Visual Studio.  
  
    1. Exclua **\Users\\**_{o nome}_**\AppData\Local\Microsoft\VisualStudio\\\*Exp**  
  
    2. Sobre o Windows **inicie** menu, escolha **todos os programas**, **SDK do Microsoft Visual Studio 2010**, **ferramentas**, **redefinir o Instância experimental**.  
  
11. Sobre o **construir** menu, escolha **recompilar solução**.  
  
## <a name="see-also"></a>Consulte também  
 [Glossário das Ferramentas de Linguagem Específica de Domínio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
