---
title: Estrutura de tópicos em um serviço de linguagem herdada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6b2ba55a2e77a1f7261812a181ad780c2ef2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726172"
---
# <a name="outlining-in-a-legacy-language-service"></a>Estrutura de tópicos em um serviço de linguagem herdado
A estrutura de tópicos torna possível recolher um programa complexo em uma visão geral ou uma estrutura de tópicos. Por exemplo, em C# todos os métodos podem ser recolhidos em uma única linha, mostrando apenas a assinatura do método. Além disso, estruturas e classes podem ser recolhidas para mostrar apenas os nomes das estruturas e classes. Dentro de um único método, a lógica complexa pode ser recolhida para mostrar o fluxo geral, mostrando apenas a primeira linha de instruções, como `foreach`, `if` e `while`.

 Os serviços de idioma herdados são implementados como parte de um VSPackage, mas a maneira mais recente de implementar recursos de serviço de linguagem é usar extensões de MEF. Para obter mais informações, consulte [Walkthrough: contorno](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Recomendamos que você comece a usar a nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de linguagem e permitirá que você aproveite os novos recursos do editor.

## <a name="enabling-support-for-outlining"></a>Habilitando o suporte para estrutura de tópicos
 A entrada de registro `AutoOutlining` é definida como 1 para habilitar a estrutura de tópicos automática. A estrutura de tópicos automática define uma análise da origem inteira quando um arquivo é carregado ou alterado para identificar regiões ocultas e mostrar os glifos de estrutura de tópicos. A estrutura de tópicos também pode ser controlada manualmente pelo usuário.

 O valor da entrada de registro `AutoOutlining` pode ser obtido por meio da propriedade <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> na classe <xref:Microsoft.VisualStudio.Package.LanguagePreferences>. A entrada de registro `AutoOutlining` pode ser inicializada com um parâmetro nomeado para o atributo <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (consulte [registrando um serviço de idioma herdado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obter detalhes).

## <a name="the-hidden-region"></a>A região oculta
 Para fornecer a estrutura de tópicos, o serviço de idioma deve dar suporte a regiões ocultas. Esses são trechos de texto que podem ser expandidos ou recolhidos. Regiões ocultas podem ser delimitadas por símbolos de idioma padrão, como chaves, ou por símbolos personalizados. Por exemplo, C# tem um `#region` / `#endregion` par que delimita uma região oculta.

 As regiões ocultas são gerenciadas por um Gerenciador de região oculta, que é exposto como a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>.

 A estrutura de tópicos usa regiões ocultas a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> e contém a extensão da região oculta, o estado atual visível e a faixa a ser mostrada quando a extensão é recolhida.

 O analisador de serviço de linguagem usa o método <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> para adicionar uma nova região oculta com o comportamento padrão para regiões ocultas, enquanto o método <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> permite que você personalize a aparência e o comportamento do contorno. Depois que as regiões ocultas são dadas à sessão de região oculta, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerencia as regiões ocultas para o serviço de idioma.

 Se você precisar determinar quando a sessão de região oculta é destruída, uma região oculta é alterada ou você precisa garantir que uma região oculta específica esteja visível; Você deve derivar uma classe da classe <xref:Microsoft.VisualStudio.Package.Source> e substituir os métodos apropriados, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> e <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, respectivamente.

### <a name="example"></a>Exemplo
 Aqui está um exemplo simplificado de criação de regiões ocultas para todos os pares de chaves. Supõe-se que a linguagem forneça correspondência de chaves e que as chaves a serem correspondidas incluam pelo menos as chaves ({e}). Essa abordagem é apenas para fins ilustrativos. Uma implementação completa teria uma manipulação completa de casos no <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Este exemplo também mostra como definir a preferência de <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> como `true` temporariamente. Uma alternativa é especificar o `AutoOutlining` parâmetro nomeado no atributo `ProvideLanguageServiceAttribute` em seu pacote de idiomas.

 Este exemplo pressupõe C# regras para comentários, cadeias de caracteres e literais.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Consulte também
- [Recursos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)