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


## Construção

### Organizational Units
<p align="center"><img src="/images/01.png?raw=true"></p>

### Project
<p align="center"><img src="/images/02.png?raw=true"></p>
<p align="center"><img src="/images/03.png?raw=true"></p>

### Data Object
<p align="center"><img src="/images/04.png?raw=true"></p>

### Ruleflow
<p align="center"><img src="/images/05.png?raw=true"></p>

### Grupo listas
<p align="center"><img src="/images/06.png?raw=true"></p>
<p align="center"><img src="/images/07.png?raw=true"></p>

### Grupo descartar
<p align="center"><img src="/images/08.png?raw=true"></p>
<p align="center"><img src="/images/09.png?raw=true"></p>
<p align="center"><img src="/images/10.png?raw=true"></p>

### Grupo analisar
<p align="center"><img src="/images/11.png?raw=true"></p>
<p align="center"><img src="/images/12.png?raw=true"></p>
<p align="center"><img src="/images/13.png?raw=true"></p>

### Decision Server
<p align="center"><img src="/images/14.png?raw=true"></p>

### Cenários de testes
<p align="center"><img src="/images/15.png?raw=true"></p>
<p align="center"><img src="/images/16.png?raw=true"></p>







