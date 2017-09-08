# BRMS Monitoramento de Operações Tesouraria

## Variáveis de entrada para cada regra
* Mesa
* Gestor
* Operador negociação
* Produto

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
