# ProjetoConceitualEcommerce
Este projeto apresenta o esquema conceitual de um banco de dados desenvolvido para gerenciar pedidos, produtos, estoques e entregas em um ambiente comercial.
Objetivo do Banco de Dados

O esquema foi projetado para atender às necessidades de uma plataforma de vendas com as seguintes funcionalidades principais:

    Gerenciamento de clientes (Pessoa Física ou Jurídica).
    Cadastro de fornecedores, vendedores terceiros e produtos.
    Registro de pedidos e rastreamento de entregas.
    Controle de estoque e alocação de produtos em diferentes locais.
    Suporte a múltiplas formas de pagamento, como cartão de crédito, boleto e Pix.

Principais Entidades e Relacionamentos
Cliente

    Representa os clientes que realizam pedidos na plataforma.
    Um cliente pode ser uma Pessoa Física (PF) ou Pessoa Jurídica (PJ), mas nunca ambos.
    O tipo de cliente é especificado através da entidade TipoCliente, com restrições para CPF (PF) ou CNPJ (PJ).

Atributos principais:

    CliID: Identificador único do cliente.
    Nome: Nome do cliente.
    TipoCliente_TipoClienteID: FK para identificar se o cliente é PF ou PJ.
    CPF/CNPJ: Restringe o cadastro ao tipo de cliente específico.

Pedido

    Representa o registro de uma compra realizada por um cliente.
    Cada pedido está relacionado a um cliente único e possui um status descritivo.

Atributos principais:

    PedidoID: Identificador único do pedido.
    PedidoStatus: Status do pedido (e.g., "Em Processamento", "Concluído").
    Cliente_CliID: FK associando o pedido ao cliente.

Forma de Pagamento

    Uma entidade independente para gerenciar as diferentes formas de pagamento de um cliente.
    Suporta múltiplos tipos de pagamento (e.g., cartão de crédito, boleto, Pix) com informações detalhadas.

Atributos principais:

    PagamentoID: Identificador único da forma de pagamento.
    TipoPagamento: Tipo de pagamento (e.g., "Cartão de Crédito").
    NumeroCartao, ValidadeCartao, CVV: Dados adicionais para cartões de crédito.
    Relacionamento com Cliente via FK.

Entrega

    Armazena informações sobre o status e o rastreamento das entregas relacionadas aos pedidos.

Atributos principais:

    EntregaID: Identificador único da entrega.
    Pedido_PedidoID: FK para associar a entrega a um pedido.
    CodigoRastreio: Código de rastreamento para acompanhamento logístico.
    StatusEntrega: Status da entrega (e.g., "Enviado", "Em Trânsito", "Entregue").

Estoque

    Controla os produtos disponíveis, organizados por local de armazenamento.
    Cada produto pode ser associado a um ou mais estoques.

Atributos principais:

    EstoqueID: Identificador único do estoque.
    Local: Descrição do local de armazenamento (e.g., "Armazém A").
    Relacionamento com Produto para mapear o número de itens disponíveis.

Produto

    Armazena as informações de produtos comercializados na plataforma.
    Produtos são associados a fornecedores e, opcionalmente, a vendedores terceiros.

Atributos principais:

    ProdutoID: Identificador único do produto.
    ProdutoCategoria: Categoria do produto (e.g., "Eletrônicos").
    Relacionamento com Fornecedor e, opcionalmente, Vendedor Terceiro.
