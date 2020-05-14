---
title: Suporte para a barra de navegação em um serviço de idioma legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704858"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Suporte para a barra de navegação em um serviço de linguagem herdado
A barra de navegação na parte superior da exibição do editor exibe os tipos e membros no arquivo. Os tipos são mostrados na gota esquerda e os membros são mostrados na gota direita. Quando o usuário seleciona um tipo, o caret é colocado na primeira linha do tipo. Quando o usuário seleciona um membro, o cuidado é colocado na definição do membro. As caixas gotas são atualizadas para refletir a localização atual do cuidador.

## <a name="displaying-and-updating-the-navigation-bar"></a>Exibindo e atualizando a barra de navegação
 Para suportar a barra de navegação, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> você deve <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> obter uma classe da classe e implementar o método. Quando o serviço de idioma é <xref:Microsoft.VisualStudio.Package.LanguageService> dado uma <xref:Microsoft.VisualStudio.Package.CodeWindowManager>janela de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> código, a classe base instancia o , que contém o objeto representando a janela de código. O <xref:Microsoft.VisualStudio.Package.CodeWindowManager> objeto recebe então <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> um novo objeto. O <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> método <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> recebe um objeto. Se você retornar uma <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> instância <xref:Microsoft.VisualStudio.Package.CodeWindowManager> de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> sua classe, o método <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> chamará [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seu método para preencher as listas internas e passa seu objeto para o gerenciador de barras abaixado. O gerenciador de barras drop-down, por sua vez, chama o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> método em seu <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto para estabelecer o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> objeto que contém as duas barras paradas.

 Quando o cuidador se <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> move, <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> o método chama o método. O <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> método base <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> chama <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> o método em sua classe para atualizar o estado da barra de navegação. Você passa um <xref:Microsoft.VisualStudio.Package.DropDownMember> conjunto de objetos para este método. Cada objeto representa uma entrada no drop-down.

## <a name="the-contents-of-the-navigation-bar"></a>O Conteúdo da Barra de Navegação
 A barra de navegação geralmente contém uma lista de tipos e uma lista de membros. A lista de tipos inclui todos os tipos disponíveis no arquivo de origem atual. Os nomes do tipo incluem as informações completas do namespace. A seguir é um exemplo de código C# com dois tipos:

```csharp
namespace TestLanguagePackage
{
    public class TestLanguageService
    {
        internal struct Token
        {
            int tokenID;
        }
        private Tokens[] tokens;
        private string serviceName;
    }
}
```

 A lista de `TestLanguagePackage.TestLanguageService` `TestLanguagePackage.TestLanguageService.Tokens`tipos será exibida e .

 A lista de membros exibe os membros disponíveis do tipo selecionado na lista de tipos. Usando o exemplo de `TestLanguagePackage.TestLanguageService` código acima, se for o tipo selecionado, a lista de membros conteria os membros `tokens` privados e `serviceName`. A estrutura `Token` interna não é exibida.

 Você pode implementar a lista de membros para tornar o nome de um membro ousado quando o cuidador é colocado dentro dele. Os membros também podem ser exibidos em texto acinzentado, indicando que eles não estão dentro do escopo onde o cuidador está atualmente posicionado.

## <a name="enabling-support-for-the-navigation-bar"></a>Habilitando o suporte para a barra de navegação
 Para habilitar o suporte para a `ShowDropdownBarOption` barra de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> navegação, você deve definir o parâmetro do atributo para `true`. Esse parâmetro define a propriedade <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Para suportar a barra de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> navegação, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> você deve <xref:Microsoft.VisualStudio.Package.LanguageService> implementar o objeto no método da classe.

 Na implementação <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> do método, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> se a `true`propriedade estiver <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> definida para , você pode retornar um objeto. Se você não devolver o objeto, a barra de navegação não será exibida.

 A opção de mostrar a barra de navegação pode ser definida pelo usuário, de modo que é possível que este controle seja redefinido enquanto a exibição do editor estiver aberta. O usuário deve fechar e reabrir a janela do editor antes que a alteração ocorra.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementando suporte para a barra de navegação
 O <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método leva duas listas (uma para cada lista baixa) e dois valores representando a seleção atual em cada lista. As listas e os valores de seleção podem ser atualizados, nesse caso o <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método deve voltar `true` para indicar que as listas foram alteradas.

 À medida que a seleção muda nos tipos de lista parada, a lista de membros deve ser atualizada para refletir o novo tipo. O que é mostrado na lista de membros pode ser:

- A lista de membros para o tipo atual.

- Todos os membros disponíveis no arquivo de origem, mas com todos os membros não no tipo atual exibidos em texto acinzentado. O usuário ainda pode selecionar os membros acinzentados, para que eles possam ser usados para navegação rápida, mas a cor indica que eles não fazem parte do tipo selecionado no momento.

  Uma implementação <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> do método normalmente executa as seguintes etapas:

1. Obtenha uma lista de declarações atuais para o arquivo de origem.

     Há várias maneiras de preencher as listas. Uma abordagem é criar um método <xref:Microsoft.VisualStudio.Package.LanguageService> personalizado em <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> sua versão da classe que chama o método com uma razão de análise personalizada que retorna uma lista de todas as declarações. Outra abordagem pode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> ser chamar <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> o método diretamente do método com a razão de análise personalizada. Uma terceira abordagem pode ser guardar <xref:Microsoft.VisualStudio.Package.AuthoringScope> as declarações na classe devolvidas <xref:Microsoft.VisualStudio.Package.LanguageService> pela última operação <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> de análise completa na classe e recuperá-lo do método.

2. Preencha ou atualize a lista de tipos.

     O conteúdo da lista de tipos pode ser atualizado quando a fonte foi alterada ou se você optou por alterar o estilo de texto dos tipos com base na posição atual do caret. Observe que esta posição <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> é passada para o método.

3. Determine o tipo a ser selecionado na lista de tipos com base na posição atual do caret.

     Você pode pesquisar as declarações obtidas na etapa 1 para encontrar o tipo que inclui a posição atual do cuidador e, em seguida, pesquisar a lista de tipos para esse tipo para determinar seu índice na lista de tipos.

4. Preencha ou atualize a lista de membros com base no tipo selecionado.

     A lista de membros reflete o que está atualmente exibido na lista suspensa dos **deputados.** O conteúdo da lista de membros pode precisar ser atualizado se a fonte foi alterada ou se você estiver exibindo apenas os membros do tipo selecionado e o tipo selecionado foi alterado. Se você optar por exibir todos os membros no arquivo de origem, então o estilo de texto de cada membro da lista precisa ser atualizado se o tipo selecionado no momento tiver sido alterado.

5. Determine o membro a ser selecionado na lista de membros com base na posição atual do caret.

     Pesquise as declarações obtidas na etapa 1 para o membro que contém a posição de cuidador atual e, em seguida, pesquise a lista de membros para que esse membro determine seu índice na lista de membros.

6. Retorne `true` se alguma alteração tiver sido feita nas listas ou nas seleções em qualquer lista.
