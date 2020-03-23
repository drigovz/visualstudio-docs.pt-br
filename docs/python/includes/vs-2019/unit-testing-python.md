---
title: Teste de unidade do código Python
description: A configuração do teste de unidade para o código Python no Visual Studio aproveita ao máximo as funcionalidades do Gerenciador de Testes para descobrir, executar e depurar testes.
ms.date: 09/18/2019
ms.topic: include
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8adce700524c4ade6c627aa91480460f8f2571f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71933470"
---
## <a name="select-the-test-framework-for-a-python-project"></a>Selecione a estrutura de teste para um projeto Python

O Visual Studio suporta duas estruturas de teste para Python, [unittest](https://docs.python.org/3/library/unittest.html) e [pytest](https://pytest.org/en/latest/) (disponível no Visual Studio 2019 a partir da versão 16.3). Por padrão, nenhuma estrutura é selecionada quando você cria um projeto Python. Para especificar uma estrutura, clique com o botão direito do mouse no nome do projeto no Solution Explorer e selecione a opção **Propriedades.** Isso abre o designer do projeto, que permite configurar testes através da guia **Teste.** A partir desta guia, você pode selecionar a estrutura de teste que deseja usar para o seu projeto. 

* Para a estrutura **de teste unitário,** o diretório raiz do projeto é usado para a descoberta de testes. Este local, bem como o padrão de texto para identificação de testes, podem ser modificados na guia **Teste** para valores especificados pelo usuário.
* Para a estrutura **pytest,** as opções de teste, como local de teste e padrões de nome de arquivo, são especificadas usando o arquivo de configuração pytest .ini padrão. Consulte a [documentação de referência pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) para obter mais detalhes.

Depois de salvar a seleção e as configurações da estrutura, a descoberta do teste será iniciada no Explorador de Testes. Se a janela Test Explorer ainda não estiver aberta, navegue até a barra de ferramentas e selecione **Test** > **Explorer**.

## <a name="configure-testing-for-python-without-a-project"></a>Configure testes para Python sem um projeto
O Visual Studio permite que você execute e teste o código Python existente sem um projeto, [abrindo uma pasta](../../quickstart-05-python-visual-studio-open-folder.md) com código Python. Nestas circunstâncias, você precisará usar um arquivo **PythonSettings.json** para configurar testes. 
1. Abra o código Python existente usando a opção **Abrir uma pasta local.** 

   ![A tela de inicialização do Visual Studio](../../media/quickstart-open-folder/01-open-local-folder.png)

1. Na janela Solution Explorer, clique no ícone **Mostrar todos os arquivos** para mostrar todos os arquivos na pasta atual.

   ![Mostrar todos os arquivos botão](../../media/unit-test-show-files.png)

1. Navegue até o arquivo **PythonSettings.json** dentro da pasta **Configurações locais.** Se você não ver esse arquivo na pasta **Configurações locais,** crie-o manualmente.
   
1. Adicione o campo **TestFramework** ao arquivo de configurações e defina-o como **pytest** ou **unittest,** dependendo da estrutura de teste que você deseja usar.

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py"
    }
    ```

    > [!Note]
    > Para a estrutura **de teste unitário,** se os campos **UnitTestRootDirectory** e **UnitTestPattern** não estiverem especificados no arquivo PythonSettings.json, eles serão adicionados e atribuídos valores padrão de "." e "test*.py" respectivamente.

1. Se sua pasta contiver um diretório **src** separado da pasta que contém seus testes, especifique o caminho para a pasta **src** usando o campo **SearchPaths** em seu arquivo **PythonSettings.json.**

    ```json
    {
    "TestFramework": "unittest",
    "UnitTestRootDirectory": "testing",
    "UnitTestPattern": "test_*.py",
    "SearchPaths": [ ".\\src"]
    }
    ```

1. Salve suas alterações no arquivo PythonSettings.json para iniciar a descoberta de teste para a estrutura especificada. 
   > [!Note]
   > Se a janela do Test Explorer já estiver **aberta, a CTRL** + **R,A** também desencadeará a descoberta.

## <a name="discover-and-view-tests"></a>Descobrir e exibir testes

Por padrão, o Visual Studio identifica os testes de teste `test` **unitário** e **pytest** como métodos cujos nomes começam com . Para ver a descoberta do teste, faça o seguinte:

1. Abra um [projeto Python](../../managing-python-projects-in-visual-studio.md).

1. Uma vez que o projeto seja carregado no Visual Studio, clique com o botão direito do mouse no projeto no Solution Explorer e selecione a estrutura **unittest** ou **pytest** na guia **Teste** de propriedades.
   > [!Note]
   > Se você usar a estrutura pytest, você pode especificar os padrões de localização de teste e nome de arquivo usando o arquivo de configuração pytest .ini padrão. Por padrão, a pasta de espaço de trabalho/projeto é usada, com um padrão de `test_*py` e `*_test.py`. Consulte a [documentação de referência pytest](https://docs.pytest.org/en/latest/reference.html#ini-options-ref) para obter mais detalhes.

1. Depois que a estrutura for selecionada, clique com o botão direito do mouse no projeto novamente e selecione **Adicionar** > **novo item**e selecione Teste de unidade **Python** seguido de **Adicionar**.

1. Essa ação cria um arquivo *test_1.py* `unittest` com código que importa `unittest.TestCase`o módulo `unittest.main()` padrão, deriva uma classe de teste e invoca se você executar o script diretamente:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Salve o arquivo, se necessário, e abra **o Test Explorer** com o comando **Test** > **Explorer** menu.

1. **Test Explorer** pesquisa seu projeto em busca de testes e os exibe como mostrado abaixo. Se você clicar duas vezes em um teste, seu arquivo de origem será aberto.

    ![Gerenciador de Testes mostrando o test_A padrão](../../media/unit-test-a-2.png) 

1. À medida que você adiciona mais testes ao seu projeto, você pode organizar a exibição no **Test Explorer** usando o menu **Grupo Por** na barra de ferramentas:

    ![Menu da barra de ferramentas Agrupar Por do Gerenciador de Testes](../../media/unit-test-group-menu-2.png) 

1. Você também pode inserir texto no campo **Pesquisar** para filtrar testes pelo nome.

Para obter mais `unittest` informações sobre o módulo e os testes de redação, consulte a [documentação python 2.7](https://docs.python.org/2/library/unittest.html) ou a [documentação Python 3.7](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Executar testes

No **Test Explorer** você pode executar testes de várias maneiras:

- **Executar Todos** claramente executa todos os testes mostrados (sujeito a filtros).
- O menu **Executar** dá-lhe comandos para executar testes com falha, aprovado ou não executar como um grupo.
- É possível selecionar um ou mais testes, clicar com o botão direito do mouse e selecionar **Executar Testes Selecionados**.

Os testes são executados em segundo plano e o **Test Explorer** atualiza o status de cada teste à medida que ele completa:

- Os testes aprovados mostram um tique verde e o tempo necessário para executar o teste:

    ![Status do test_A aprovado](../../media/unit-test-A-pass.png)

- Os testes com falha mostram uma cruz vermelha com um link **Saída** que mostra a saída do console e a saída `unittest` da execução de teste:

    ![Status do test_A com falha](../../media/unit-test-A-fail.png)

    ![test_A com falha com motivo](../../media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Depurar testes

Como os testes de unidade são partes do código, eles estão sujeitos a bugs, assim como qualquer outro código e, ocasionalmente, precisam ser executados em um depurador. No depurador é possível definir pontos de interrupção, examinar variáveis e executar o código em etapas. O Visual Studio também fornece ferramentas de diagnóstico para testes de unidade.

> [!Note]
> Por padrão, a depuração de teste usa o depurador ptvsd 4. Se você quiser usar o PTVsd 3, você pode selecionar a opção **Usar depurador legado** **na** > **depuração****de opções** > de ferramentas**Python** > . 

Para iniciar a depuração, defina um ponto de ruptura inicial em seu código e clique com o botão direito do mouse no teste (ou uma seleção) no **Test Explorer** e selecione **Debug Selected Tests**. O Visual Studio inicia o depurador do Python como faria com o código do aplicativo.

![Depurando um teste](../../media/unit-test-debugging.png)

Você também pode usar a **Cobertura de Código de Análise para Testes Selecionados**. Para obter mais informações, confira [Usar a cobertura de código para determinar quanto do código está sendo testado](../../../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).
