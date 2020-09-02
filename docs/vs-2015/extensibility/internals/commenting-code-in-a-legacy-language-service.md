---
title: Comentando o código em um serviço de linguagem herdado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1405456ca9a6ba00926c82bcc7959ea36d26c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160914"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Comentando o código em um serviço de linguagem herdado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Linguagens de programação normalmente fornecem um meio de anotar ou comentar o código. Um comentário é uma seção de texto que fornece informações adicionais sobre o código, mas é ignorada durante a compilação ou interpretação.  
  
 As classes do MPF (estrutura de pacote gerenciada) fornecem suporte para comentar e remover comentários do texto selecionado.  
  
## <a name="comment-styles"></a>Estilos de comentário  
 Há dois estilos gerais de comentário:  
  
1. Comentários de linha, onde o comentário está em uma única linha.  
  
2. Bloquear comentários, onde o comentário pode incluir várias linhas.  
  
   Os comentários de linha normalmente têm um caractere inicial (ou caracteres), enquanto os comentários de bloco têm caracteres de início e término. Por exemplo, em C#, um comentário de linha começa com//e um comentário de bloco começa com/* e termina com \* /.  
  
   Quando o usuário seleciona a **seleção de comentário** do comando no menu **Editar**  ->  **avançado** , o comando é roteado para o <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> método na <xref:Microsoft.VisualStudio.Package.Source> classe. Quando o usuário seleciona a **seleção Remover comentário**do comando, o comando é roteado para o <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> método.  
  
## <a name="supporting-code-comments"></a>Comentários de código de suporte  
 Você pode fazer com que o serviço de linguagem dê suporte a comentários de código por meio do `EnableCommenting` parâmetro nomeado do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Isso define a <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propriedade da <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Para obter mais informações sobre como definir recursos de servicce de idioma, consulte [registrando um serviço de idioma herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Você também deve substituir o <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método para retornar uma <xref:Microsoft.VisualStudio.Package.CommentInfo> estrutura com os caracteres de comentário para seu idioma. Os caracteres de comentário de linha de estilo C# são o padrão.  
  
### <a name="example"></a>Exemplo  
 Aqui está um exemplo de implementação do <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> método.  
  
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
  
## <a name="see-also"></a>Consulte Também  
 [Recursos do serviço de linguagem herdada](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service1.md)
