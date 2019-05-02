---
title: Visão geral da análise de código gerenciado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a38909eb0917b3ad5b02d5e953c17c950c7c819e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539147"
---
# <a name="code-analysis-for-managed-code-overview"></a>Visão geral da análise de código para código gerenciado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A análise de código gerenciado analisa os assemblies gerenciados e relata informações sobre assemblies, como violações das regras de programação e de design estabelecidas nas Diretrizes de Design do Microsoft .NET Framework.  
  
 A ferramenta de análise representa as verificações que executa durante uma análise como mensagens de aviso. As mensagens de aviso identificam problemas de programação e de design relevantes e, quando possível, fornecem informações de como corrigir o problema.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integração ao IDE (ambiente de desenvolvimento integrado)  
 Como desenvolvedor, você pode executar a análise de código no projeto automaticamente ou manualmente.  
  
 Para executar a análise de código sempre que você compilar um projeto, selecione **Habilitar a análise de código no build (define a constante CODE_ANALYSIS)** na página de propriedades do projeto. Para obter mais informações, confira [Como: habilitar e desabilitar a análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Para executar a análise de código manualmente em um projeto, no menu **Analisar**, clique em **Executar análise de código no**_ProjectName_. Para obter mais informações, confira [Como: habilitar e desabilitar a análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Conjuntos de regras  
 As regras de análise de código gerenciado são agrupadas em *conjuntos de regras*. Você pode usar um dos conjuntos de regras padrão da Microsoft ou criar um conjunto de regras personalizado definido para atender a uma necessidade específica. Para obter mais informações, confira [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>Supressão no código-fonte  
 Geralmente, é útil indicar que um aviso não é aplicável. Isso informa ao desenvolvedor e a outras pessoas que poderão examinar o código mais tarde, que um aviso foi investigado e, em seguida, suprimido ou ignorado.  
  
 A supressão de avisos no código-fonte é implementada por meio de atributos personalizados. Para suprimir um aviso, adicione o atributo `SuppressMessage` ao código-fonte, conforme é mostrado no exemplo a seguir:  
  
 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```
  
 Para obter mais informações, confira [Suprimir avisos usando o atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Executar análise de código como parte da política de check-in  
 Em uma organização, talvez convenha exigir que todos os check-ins satisfaçam determinadas políticas. Especificamente, convém garantir que estas políticas sejam seguidas:  
  
- não há nenhum erro de build no check-in do código.  
  
- A análise de código é executada como parte do build mais recente.  
  
  Você pode garantir isso especificando políticas de check-in. Para obter mais informações, confira [Melhorando a qualidade do código com políticas de check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integração ao Team Build  
 Você pode usar os recursos integrados do sistema de build para executar a ferramenta de análise como parte do processo de build. Para obter mais informações, consulte [Compilar o aplicativo](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="see-also"></a>Consulte também  
 [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Como: habilitar e desabilitar a análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
