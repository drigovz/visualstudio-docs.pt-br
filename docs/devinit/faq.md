---
title: Perguntas frequentes
description: Perguntas frequentes sobre a ferramenta devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2b482de4dd6c72aa744ef92563b8c1f23febbdd1
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005000"
---
# <a name="frequently-asked-questions-for-devinit"></a>Perguntas frequentes sobre o devinit

## <a name="is-devinit-just-for-github-codespaces"></a>É devinit apenas para Codespaces do GitHub?

Por enquanto, o devinit só está disponível como parte da versão beta particular do GitHub Codespaces. No entanto, temos planos de incluir devinit em uma próxima versão do Visual Studio 2019.

## <a name="is-it-windows-only"></a>É apenas o Windows?
Sim, o devinit se concentra na criação de ambientes de desenvolvedor que funcionam para os desenvolvedores que usam o Visual Studio, o que significa o Windows. Estamos considerando outras plataformas, mas muitas delas já têm ótimas soluções em vigor, portanto, queríamos começar com o Visual Studio e o Windows.

## <a name="theres-no-tool-for-the-dependency-i-need"></a>Não há nenhuma ferramenta para a dependência que preciso!

Lamentamos! Se você fizer parte da versão beta particular do GitHub Codespaces, poderá voltar para nós por meio do canal de comentários para a versão beta privada. Se você não fizer parte da versão beta privada, ainda adoraremos seus comentários sobre o que você precisa, e você poderá arquivar um problema em nossos [documentos do Visual Studio](https://github.com/MicrosoftDocs/visualstudio-docs/) com o rótulo `devinit` para solicitar suporte para a ferramenta de que você precisa.

## <a name="something-went-wrong-how-do-i-debug"></a>Algo deu errado, como faço para depurar?

Se devinit estiver falhando, a primeira coisa a ser tentada é o `--verbose / -v` sinalizador para obter mais informações. É provável que a ferramenta subjacente que devinit está chamando esteja encontrando um problema. As informações detalhadas do log devem incluir uma pista sobre onde procurar em seguida.

## <a name="why-not-just-a-script"></a>Por que não apenas um script?

A configuração de ambientes por meio de um script é uma técnica de tempo antiga e pode funcionar muito bem. Se funcionar para você, use-o! devinit é outra opção para desenvolvedores para quando os scripts não são a melhor opção.

## <a name="why-not-a-container"></a>Por que não é um contêiner?

Os contêineres e o Docker são excelentes ferramentas para implantar um ambiente por meio de código. Há alguns motivos pelos quais os contêineres podem não ser a solução certa para você:

1. Se você quiser usar um ambiente de desenvolvimento baseado na área de trabalho do Windows.
1. Se você já tiver um sistema operacional e quiser apenas ajustá-lo em vez de implantar um novo ambiente.

Por esses motivos, o devinit é sobre a personalização do ambiente do Windows que você tem atualmente.

## <a name="what-about-other-vm-creation-tools-for-example-terraform-packer-chef-vagrant-etc"></a>E quanto a outras ferramentas de criação de VM (por exemplo, Terraform, Packer, chefe, Vagrant, etc.)

Há muitas ferramentas excelentes para criar imagens do Windows e você deve usá-las! No entanto, não foi possível encontrar um que atendesse a todos os cenários que tínhamos em mente. Queremos que o devinit seja uma ferramenta para que os desenvolvedores personalizem seu ambiente com tudo o que for necessário para um determinado repositório e tenham uma ótima integração com o Visual Studio, em vez de ser uma ferramenta para criar imagens de VM.

## <a name="what-about-winget"></a>E quanto a Winget?

devinit não é um Gerenciador de pacotes como Winget e não queremos que ele seja. Queremos que você possa usar o Winget com devinit e estamos trabalhando em uma ferramenta apenas para isso.

## <a name="how-are-restarts-handled"></a>Como as reinicializações são tratadas?

Se qualquer coisa que o devinit instalar exigir uma reinicialização do sistema operacional, uma mensagem de erro será emitida para o console. Em seguida, você precisará reinicializar o sistema operacional de cada vez que se adequar a você. Após a reinicialização, talvez seja necessário executar novamente o devinit se todas as dependências não tiverem sido instaladas.

## <a name="working-with-others"></a>Trabalhando com outras pessoas

devinit é tudo sobre a habilitação do uso do ecossistema amplo que está lá para implantar e configurar as dependências que seu aplicativo pode ter. Embora o devinit tenha uma opinião sobre o que ele fornece, o devinit se refere principalmente a permitir que outras ferramentas sejam executadas a partir de um arquivo JSON declarativo.

Hoje, a devinit está apenas começando e nossa [lista de ferramentas](devinit-tool-list.md) é apenas um começo.
