---
layout: LandingPage
title: Controle de versão
description: Guia de introdução ao controle de versão no Visual Studio
keywords: VSTS, TFS, Controle de Versão
author: steved0x
ms.manager: jillfra
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: 805fe86fcbebdfeb3747dd593d9abbf0f641212d
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160022"
---
# <a name="version-control-in-visual-studio"></a>Controle de Versão no Visual Studio

Os sistemas de controle de versão ajudam você a controlar as alterações de código ao longo do tempo. Ao fazer as alterações, o sistema de controle de versão tira um instantâneo dos seus arquivos. O sistema de controle de versão guarda o instantâneo permanentemente, para que você possa revisá-lo, se precisar. O Visual Studio fornece [Controle de Versão do Git](/azure/devops/repos/tfvc/index?view=vsts) e do [Team Foundation (TFVC)](/azure/devops/repos/git/index?view=vsts) no mesmo projeto. Para decidir entre os dois sistemas, consulte [Escolhendo o controle da versão correto para seu projeto](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json).

## <a name="git"></a>Git

Git é o sistema de controle de versão mais usado atualmente e está se tornando rapidamente o padrão para controle de versão. Git é um sistema de controle de versão distribuído, ou seja, sua cópia local do código é um repositório de controle da versão completa. Estes repositórios locais totalmente funcionais facilitam o trabalho offline ou remoto. Você confirma seu trabalho localmente e depois sincroniza sua cópia do repositório com a cópia no servidor. Esse paradigma é diferente do controle de versão centralizado, no qual os clientes devem sincronizar o código com um servidor antes de criar novas versões do código.

<!-- markdownlint-disable MD033 -->
<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Git logo" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Aprender sobre o Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Git logo" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Introdução ao Git no Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Git logo" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Clonar um repositório Git existente</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

O Controle de Versão do Team Foundation (TFVC) é um sistema de controle de versão centralizado. Normalmente, os membros da equipe têm somente uma versão de cada arquivo nos computadores de desenvolvimento. Os dados históricos são mantidos somente no servidor. As ramificações são baseadas em caminho e criadas no servidor.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Visual Studio logo" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Aprender sobre TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Visual Studio logo" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Introdução ao TFVC no Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="Visual Studio logo" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Examinar seu código</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="resources"></a>Recursos

- [Catálogo do Pro Git](https://git-scm.com/book/en/v2)
- [Planejar sua migração para Git](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [Migrar do TFVC para o Git](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)
- [Controle de versão (Visual Studio para Mac)](/visualstudio/mac/version-control)