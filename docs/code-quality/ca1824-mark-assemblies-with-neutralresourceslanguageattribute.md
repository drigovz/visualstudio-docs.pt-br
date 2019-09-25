---
title: 'CA1824: Marque assemblies com NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df5c0db4e9e141e5833893bbbb447328eab8851e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233351"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Marque assemblies com NeutralResourcesLanguageAttribute

|||
|-|-|
|NomeDoTipo|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um assembly contém um recurso baseado em **resx**, mas não tem o <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> aplicado a ele.

## <a name="rule-description"></a>Descrição da regra

O <xref:System.Resources.NeutralResourcesLanguageAttribute> atributo informa o Gerenciador de recursos da cultura padrão de um aplicativo. Se os recursos da cultura padrão forem inseridos no assembly principal do aplicativo e <xref:System.Resources.ResourceManager> tiver que recuperar recursos que pertençam à mesma cultura que a cultura padrão, o <xref:System.Resources.ResourceManager> usará automaticamente os recursos localizados no assembly principal em vez de procurar por um assembly satélite. Isso ignora a investigação de assembly usual, melhora o desempenho da pesquisa para o primeiro recurso que você carrega e pode reduzir seu conjunto de trabalho.

> [!TIP]
> Consulte [empacotando e implantando recursos](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) para o <xref:System.Resources.ResourceManager> processo que o usa para investigar os arquivos de recurso.

## <a name="fix-violations"></a>Corrigir violações

Para corrigir uma violação dessa regra, adicione o atributo ao assembly e especifique o idioma dos recursos da cultura neutra.

### <a name="to-specify-the-neutral-language-for-resources"></a>Para especificar o idioma neutro para recursos

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse em seu projeto e selecione **Propriedades**.

2. Selecione a guia **aplicativo** e, em seguida, selecione **informações do assembly**.

   > [!NOTE]
   > Se o seu projeto for um projeto .NET Standard ou .NET Core, selecione a guia **pacote** .

3. Selecione o idioma na lista suspensa **idioma neutro** ou **idioma neutro do assembly** .

4. Selecione **OK**.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É permitido suprimir um aviso dessa regra. No entanto, o desempenho da inicialização pode ser prejudicado.

## <a name="see-also"></a>Consulte também

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Recursos em aplicativos da área de trabalho (.NET)](/dotnet/framework/resources/)
- [CA1703-as cadeias de caracteres de recursos devem ser digitadas corretamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701-palavras compostas da cadeia de caracteres de recurso devem estar em algum meio correto](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)