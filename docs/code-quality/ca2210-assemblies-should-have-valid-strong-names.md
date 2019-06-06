---
title: 'CA2210: Assemblies devem ter nomes fortes válidos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89edba30a95d61268aebb26de8d973f6201c0fcf
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714757"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Assemblies devem ter nomes fortes válidos

|||
|-|-|
|NomeDoTipo|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Categoria|Microsoft.Design|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Um assembly não está assinado com um nome forte, o nome forte não pôde ser verificado ou o nome forte não é válido sem as configurações do registro atual do computador.

## <a name="rule-description"></a>Descrição da regra

Esta regra recupera e verifica o nome forte de um assembly. Ocorre uma violação se qualquer uma das seguintes opções for verdadeira:

- O assembly não tem um nome forte.

- O assembly foi alterado depois de entrar.

- O assembly é assinado com atraso.

- O assembly foi assinado incorretamente ou a assinatura falhou.

- O assembly requer configurações do registro para passar pela verificação. Por exemplo, a ferramenta de nome forte (Sn.exe) foi usada para ignorar a verificação para o assembly.

O nome forte protege clientes do carregamento desconhecido de um assembly adulterado. Os assemblies sem nomes fortes não devem ser implantados fora de cenários muito limitados. Se você compartilhar ou distribuir assemblies não assinados corretamente, o assembly poderá ser adulterado, o Common Language Runtime poderá não carregar o assembly ou o usuário talvez precise desabilitar a verificação em seu computador. Um assembly sem um nome forte tem das seguintes desvantagens:

- Não não possível verificar suas origens.

- O common language runtime não pode avisar os usuários se o conteúdo do assembly tiver sido alterado.

- Ele não pode ser carregado no cache de assembly global.

Observe que, para carregar e analisar um assembly assinado com atraso, você deve desabilitar verificação para o assembly.

## <a name="how-to-fix-violations"></a>Como corrigir violações

### <a name="create-a-key-file"></a>Criar um arquivo de chave

Use um dos procedimentos a seguir:

- Use o [ferramenta de vinculador de Assembly (Al.exe)](/dotnet/framework/tools/al-exe-assembly-linker).

- Para o .NET Framework 2.0, use o `/keyfile` ou `/keycontainer` opção de compilador [/KEYFILE (especificar chave ou par de chaves para assinar um Assembly)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) ou [/KEYCONTAINER (especificar um contêiner de chave para assinar um Assembly)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) opção de vinculador em C++).

- Para o .NET Framework v 1.0 ou 1.1, use o <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> ou <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atributo.

### <a name="sign-your-assembly-with-a-strong-name-in-visual-studio"></a>Assinar o assembly com um nome forte no Visual Studio

1. No Visual Studio, abra sua solução.

2. Na **Gerenciador de soluções**, clique em seu projeto e, em seguida, clique em **propriedades.**

3. Clique o **Signing** guia e, em seguida, selecione o **assinar o assembly** caixa de seleção.

4. Partir **escolher um arquivo de chave de nome forte**, selecione **New**.

   O **criar chave de nome forte** janela será exibida.

5. Na **nome do arquivo de chave**, digite um nome para sua chave de nome forte.

6. Escolha se deseja proteger a chave com uma senha e, em seguida, clique em **Okey**.

7. Na **Gerenciador de soluções**, clique em seu projeto e, em seguida, clique em **Build**.

### <a name="sign-your-assembly-with-a-strong-name-outside-visual-studio"></a>Assinar o assembly com um nome forte fora do Visual Studio

Use o [ferramenta de nome forte (Sn.exe)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Suprimir um aviso nessa regra somente se o assembly é usado em um ambiente em que viole o conteúdo não é uma preocupação.

## <a name="see-also"></a>Consulte também

- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>
- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
- [Como: assinar um assembly com um nome forte](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sn.exe (Ferramenta Nome Forte)](/dotnet/framework/tools/sn-exe-strong-name-tool)