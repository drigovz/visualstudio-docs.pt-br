---
title: Código de reformatação em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705918"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Reformatando o código em um serviço de linguagem herdado

No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] código fonte pode ser reformatado normalizando o uso de recuos e espaço em branco. Isso pode incluir inserir ou remover espaços ou guias no início de cada linha, adicionar novas linhas entre linhas ou substituir espaços por guias ou guias por espaços.

> [!NOTE]
> Inserir ou excluir caracteres newline pode afetar marcadores como pontos de interrupção e marcadores, mas adicionar ou remover espaços ou guias não afeta marcadores.

Os usuários podem iniciar uma operação de reformatação selecionando **Seleção de formato** ou documento de **formato** no menu **Avançado** no menu **Editar.** Uma operação de reformatação também pode ser acionada quando um trecho de código ou um caractere em particular é inserido. Por exemplo, quando você digita uma cinta de fechamento em C#, tudo entre a cinta aberta correspondente e a cinta de fechamento é automaticamente recuado para o nível adequado.

Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] envia o comando **'Seleção de formato'** <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> ou documento <xref:Microsoft.VisualStudio.Package.Source> **de formato** para o serviço de idiomas, a <xref:Microsoft.VisualStudio.Package.ViewFilter> classe chama o método na classe. Para suportar a formatação, <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> você deve substituir o método e fornecer seu próprio código de formatação.

## <a name="enabling-support-for-reformatting"></a>Habilitando o apoio à reformatação

Para suportar a `EnableFormatSelection` formatação, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> o parâmetro `true` do deve ser definido para quando você registrar seu VSPackage. Isso define <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> a `true`propriedade para . O <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> método devolve o valor desta propriedade. Se ele voltar <xref:Microsoft.VisualStudio.Package.ViewFilter> a verdade, a classe chama o <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.

## <a name="implementing-reformatting"></a>Implementando reformatação

Para implementar a reformatação, você deve <xref:Microsoft.VisualStudio.Package.Source> derivar uma <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> classe da classe e substituir o método. O <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> objeto descreve o comprimento <xref:Microsoft.VisualStudio.Package.EditArray> para o formato e o objeto contém as edições feitas no vão. Observe que esse período pode ser o documento inteiro. No entanto, uma vez que é provável que haja várias alterações feitas no período, todas as alterações devem ser reversíveis em uma única ação. Para fazer isso, enrole <xref:Microsoft.VisualStudio.Package.CompoundAction> todas as alterações em um objeto (consulte a seção "Usando a classe CompoundAction" neste tópico).

### <a name="example"></a>Exemplo

O exemplo a seguir garante que há um único espaço após cada comuma na seleção, a menos que a comma seja seguida por uma guia ou esteja no final da linha. Os espaços de arrasto após a última comma em uma linha são excluídos. Consulte a seção "Usando a classe CompoundAction" neste tópico <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> para ver como esse método é chamado a partir do método.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>Usando a classe CompoundAction

Toda a reformatação feita em uma seção de código deve ser reversível em uma única ação. Isso pode ser <xref:Microsoft.VisualStudio.Package.CompoundAction> feito usando uma aula. Esta classe envolve um conjunto de operações de edição no buffer de texto em uma única operação de edição.

### <a name="example"></a>Exemplo

Aqui está um exemplo de <xref:Microsoft.VisualStudio.Package.CompoundAction> como usar a classe. Veja o exemplo na seção "Implementando suporte para formatação" neste tópico para um exemplo do `DoFormatting` método.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>Confira também

- [Recursos do serviço de linguagem herdado](legacy-language-service-features1.md)
