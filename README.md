# BRMS Monitoramento de Operações Tesouraria

## Listas de Apoio Parâmetros

### Operador de Negociação - Cambio
* Operador Cambio 1
* Operador Cambio 2
* Operador Cambio 3
* Operador Cambio 4
* Operador Cambio 5

### Produtos Autorizados – Cambio
* Produto Cambio 1
* Produto Cambio 2
* Produto Cambio 3
* Produto Cambio 4
* Produto Cambio 5

## Variáveis de entrada para cada regra
* Mesa
* Gestor
* Operador negociação
* Produto

## Árvores de Decisão

### Árvore de decisão Estratégia X Gestor	
```
IF (Mesa = “CAMBIO” 	OU  Mesa =  “FX”)		=	VERDADEIRO	AND
    (Gestor = “CAMBIO”	OU Gestor = “HEDGE”)		=	VERDADEIRO	
	ENTÃO	
		S: Descarta
	SE NÃO	
		N: Retorna para análise
```

### Árvore de decisão Produto X Gestor		
```
IF (Mesa = “CAMBIO” 	OU  Mesa =  “FX”)				     = VERDADEIRO	AND
    (Operador Negociação contém Lista Operador  de Negociação – Cambio) = VERDADEIRO	AND
    (Produto contém Lista Produtos Autorizados –  Cambio) 		     = VERDADEIRO	
	ENTÃO	
		S: Descarta
	SE NÃO	
		N: Retorna pra análise
```

### Árvore de decisão Operador X Gestor	
```
IF (Mesa = “CAMBIO” 	OU  Mesa =  “FX”)				      =	VERDADEIRO	AND
    (Operador Negociação contém Lista Operador  de Negociação – Cambio)  =	VERDADEIRO	
	ENTÃO	
		S: Descarta
	SE NÃO	
		N: Retorna pra análise
```

## Cenários de Testes

### Cenário 1
Variáveis de Entrada: 
```
Mesa 			= “EMPRESTIMOS”
Gestor 			= “CAMBIO”
Operador negociação	= “OPERADOR CAMBIO 1”
Produto 		= “PRODUTO CAMBIO 1”
```
Resultado Esperado:
```
Árvore de decisão Estratégia X Gestor >> RETORNAR PARA ANÁLISE
Árvore de decisão Produto X Gestor    >> Retornar para análise
Árvore de decisão Operador X Gestor >> Retorna para análise
```

### Cenário 2
Variáveis de Entrada: 
```
Mesa 			= “FX”
Gestor 			= “CAMBIO”
Operador negociação 	= “OPERADOR CAMBIO 1”
Produto 		= “PRODUTO CAMBIO 6”
```
Resultado Esperado :
```
Árvore de decisão Estratégia X Gestor	>> Descarta
Árvore de decisão Produto X Gestor	>> Retorna pra análise
Árvore de decisão Operador X Gestor	>> Descarta
```
## Execução dos Testes

### URL Post
http://localhost:8080/kie-server/services/rest/server/containers/instances/tesouraria

### Teste 1
```
<batch-execution lookup="mySession">
<insert out-identifier="o1">
	<com.redhat.tesouraria.Operacao>
		<mesa>CAMBIO</mesa>
		<gestor>CAMBIO</gestor>
	</com.redhat.tesouraria.Operacao>
</insert>
<start-process processId="tesouraria.Fluxo">
</start-process>
<fire-all-rules />
</batch-execution>
```

### Teste 2
```
<batch-execution lookup="mySession">
<insert out-identifier="o1">
	<com.redhat.tesouraria.Operacao>
		<mesa>CAMBIO</mesa>
		<operador>Operador Cambio 3</operador>
		<produto>Produto Cambio 1</produto>
	</com.redhat.tesouraria.Operacao>
</insert>
<start-process processId="tesouraria.Fluxo">
</start-process>
<fire-all-rules />
</batch-execution>
```

### Teste 3
```
<batch-execution lookup="mySession">
<insert out-identifier="o1">
	<com.redhat.tesouraria.Operacao>
		<mesa>EMPRESTIMOS</mesa>
		<gestor>CAMBIO</gestor>
		<operador>Operador Cambio 1</operador>
		<produto>Produto Cambio 1</produto>
	</com.redhat.tesouraria.Operacao>
</insert>
<start-process processId="tesouraria.Fluxo">
</start-process>
<fire-all-rules />
</batch-execution>
```

### Teste 4
```
<batch-execution lookup="mySession">
<insert out-identifier="o2">
	<com.redhat.tesouraria.Operacao>
		<mesa>FX</mesa>
		<gestor>CAMBIO</gestor>
		<operador>Operador Cambio 1</operador>
		<produto>Produto Cambio 6</produto>
	</com.redhat.tesouraria.Operacao>
</insert>
<start-process processId="tesouraria.Fluxo">
</start-process>
<fire-all-rules />
</batch-execution>
```

### Teste 5
```
<batch-execution lookup="mySession">
<insert out-identifier="o1">
	<com.redhat.tesouraria.Operacao>
		<mesa>EMPRESTIMOS</mesa>
		<gestor>CAMBIO</gestor>
		<operador>Operador Cambio 1</operador>
		<produto>Produto Cambio 1</produto>
	</com.redhat.tesouraria.Operacao>
</insert>
<insert out-identifier="o2">
	<com.redhat.tesouraria.Operacao>
		<mesa>FX</mesa>
		<gestor>CAMBIO</gestor>
		<operador>Operador Cambio 1</operador>
		<produto>Produto Cambio 6</produto>
	</com.redhat.tesouraria.Operacao>
</insert>
<start-process processId="tesouraria.Fluxo">
</start-process>
<fire-all-rules />
</batch-execution>
```
