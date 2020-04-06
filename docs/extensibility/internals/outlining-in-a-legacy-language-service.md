---
title: Delineando em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706806"
---
# <a name="outlining-in-a-legacy-language-service"></a>Estrutura de tópicos em um serviço de linguagem herdado
O delineamento torna possível desabar um programa complexo em uma visão geral ou contorno. Por exemplo, em C# todos os métodos podem ser colapsados para uma única linha, mostrando apenas a assinatura do método. Além disso, estruturas e classes podem ser colapsadas para mostrar apenas os nomes das estruturas e classes. Dentro de um único método, a lógica complexa pode ser colapsada `foreach` `if`para `while`mostrar o fluxo global mostrando apenas a primeira linha de afirmações, tais como , e .

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais, consulte [Passo a Passo: Delineando](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="enabling-support-for-outlining"></a>Habilitando o suporte para desalinhar
 A `AutoOutlining` entrada de registro é definida como 1 para habilitar o delineamento automático. O delineamento automático configura uma análise de toda a fonte quando um arquivo é carregado ou alterado para identificar regiões ocultas e mostrar os glifos delineamento. O delineamento também pode ser controlado manualmente pelo usuário.

 O valor `AutoOutlining` da entrada do registro <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> pode ser <xref:Microsoft.VisualStudio.Package.LanguagePreferences> obtido através do imóvel da classe. A `AutoOutlining` entrada de registro pode ser inicializada <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> com um parâmetro nomeado para o atributo (consulte [Registrando um Serviço de Linguagem Legado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obter detalhes).

## <a name="the-hidden-region"></a>A Região Oculta
 Para fornecer delineamento, seu serviço de idiomas deve suportar regiões ocultas. São períodos de texto que podem ser expandidos ou colapsados. Regiões ocultas podem ser delimitadas por símbolos de linguagem padrão, como chaves ou por símbolos personalizados. Por exemplo, C# `#region` / `#endregion` tem um par que delimita uma região oculta.

 As regiões ocultas são gerenciadas por um gerenciador de região oculta, que é exposto como a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interface.

 O delineamento usa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> regiões ocultas da interface e contém o vão da região oculta, o estado visível atual e o banner a ser mostrado quando o vão é colapsado.

 O analisador de <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> serviços de idiomausa o método para adicionar uma <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> nova região oculta com o comportamento padrão para regiões ocultas, enquanto o método permite personalizar a aparência e o comportamento do contorno. Uma vez que as regiões ocultas são dadas à sessão da região oculta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerencia as regiões ocultas para o serviço de idiomas.

 Se você precisar determinar quando a sessão da região oculta é destruída, uma região oculta é alterada ou você precisa ter certeza de que uma determinada região oculta é visível; você deve derivar <xref:Microsoft.VisualStudio.Package.Source> uma classe da classe e <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>substituir <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>os métodos apropriados, e , respectivamente.

### <a name="example"></a>Exemplo
 Aqui está um exemplo simplificado de criação de regiões ocultas para todos os pares de chaves. Presume-se que a linguagem fornece correspondência de aparelhos, e que os aparelhos a serem combinados incluem pelo menos os aparelhos encaracolados ({ e }). Esta abordagem é apenas para fins ilustrativos. Uma implementação completa teria um tratamento <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>completo dos casos em . Este exemplo também mostra <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> como `true` definir a preferência para temporariamente. Uma alternativa é `AutoOutlining` especificar o `ProvideLanguageServiceAttribute` parâmetro nomeado no atributo no seu pacote de idioma.

 Este exemplo assume regras C# para comentários, strings e literais.

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

## <a name="see-also"></a>Confira também
- [Recursos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)
