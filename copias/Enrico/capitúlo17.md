Capitúlo 17
## O Sistema de Impressão (CUPS)
O Common Unix Printing System (CUPS) é o padrão para gerenciar impressoras no Linux.

Acesso: Pode ser gerenciado via interface web através do endereço localhost:631.

## Comandos de Linha de Comando:
lp e lpr: Enviam documentos para a fila de impressão.
lpoptions: Configura opções de impressão e define a impressora padrão.

Compatibilidade: Oferece suporte tanto para a interface System V quanto para a BSD

## Formatos de Documentos
PostScript: Linguagem focada em qualidade, excelente para dimensionar fontes e gráficos vetoriais.

PDF (Portable Document Format): O padrão universal para troca de documentos, garantindo que o arquivo tenha a mesma aparência em qualquer dispositivo.

## Ferramentas de Conversão e Edição
O Linux possui ferramentas poderosas para manipular esses formatos sem precisar de softwares pesados:

## Ferramentas de Gerenciamento de Documentos e Impressão

| Ferramenta | Função Principal |
| :--- | :--- |
| **CUPS** | Sistema de impressão acessível via `localhost:631`. |
| **lp / lpr** | Comandos para enviar documentos para a impressora. |
| **lpoptions** | Define opções e valores padrão da impressora. |
| **enscript** | Converte arquivos de texto para PostScript e outros formatos. |
| **pdftk** | Manipula PDFs: une, divide, criptografa, extrai páginas e corrige arquivos. |
| **pdfinfo** | Extrai metadados e informações técnicas de documentos PDF. |
| **flpsed** | Adiciona dados a documentos PostScript. |
| **pdfmod** | Interface gráfica para modificar e organizar páginas de PDFs. |