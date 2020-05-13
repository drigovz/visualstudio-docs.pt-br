---
title: Código de comentários em um serviço de linguagem legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709432"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Código de comentário em um serviço de linguagem legado
As linguagens de programação normalmente fornecem um meio de anotar ou comentar o código. Um comentário é uma seção de texto que fornece informações adicionais sobre o código, mas é ignorado durante a compilação ou interpretação.

 As classes de quadro de pacote gerenciado (MPF) fornecem suporte para comentar e não comentar texto seleto.

## <a name="comment-styles"></a>Estilos de comentário
Existem dois estilos gerais de comentário:

1. Comentários de linha, onde o comentário está em uma única linha.

2. Bloquear comentários, onde o comentário pode incluir várias linhas.

Os comentários de linha normalmente têm um caractere inicial (ou caracteres), enquanto os comentários de bloco têm caracteres de início e de fim. Por exemplo, em C#, um `//`comentário de linha `/*` começa com `*/`, e um comentário de bloco começa com e termina com .

Quando o usuário seleciona o comando **Seleção** de comentários no <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> menu <xref:Microsoft.VisualStudio.Package.Source> **Editar** > **avançado,** o comando é encaminhado para o método na classe. Quando o usuário seleciona o comando **Sem comentar Seleção,** o comando é encaminhado para o <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> método.

## <a name="support-code-comments"></a>Comentários de código de suporte
 Você pode ter seus comentários de código `EnableCommenting` de suporte <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> de serviço de idioma por meio do parâmetro nomeado do . Isso define <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> a <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriedade da classe. Para obter mais informações sobre como definir os recursos do serviço de idioma, consulte [Registre um serviço de idioma legado](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Você também deve <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> substituir o <xref:Microsoft.VisualStudio.Package.CommentInfo> método para retornar uma estrutura com os caracteres de comentário para o seu idioma. Caracteres de comentário da linha c#-style são o padrão.

### <a name="example"></a>Exemplo
 Aqui está um exemplo <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> de implementação do método.

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>Confira também
- [Recursos de serviço de idioma legado](../../extensibility/internals/legacy-language-service-features1.md)
- [Registre um serviço de idioma legado](../../extensibility/internals/registering-a-legacy-language-service1.md)
