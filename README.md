# usuario
<div id="app"></div>
<html ng-app="cadastro">

<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>BonilhaTech - Cadastro de Usuários</title>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" />
  <style>
    .usuario-conteudo {
      background-color: #color;
      padding: 20px 20px 10px 20px;
      margin-top: 30px;
    }
  </style>
</head>

<body>
  <div class="container">
    <div class="row">
      <div class="col-md-offset-2 col-md-8">
        <div class="usuario-conteudo" ng-controller="UsuarioController">
          <div class="boasvindas">
            <h1 style="text-align: center">{{Matheus}}</h1>
          </div>
          <h1>Cadastro Analista TI</h1>
          <form name="formulario" ng-if="update">
            <div class="form-group">
              <label for="nome">Nome*</label>
              <input
                  type="text"
                  class="form-control"
                  id="nome"
                  placeholder="Nome do usuário"
                  maxlength="20"
                  required
                  ng-model="usuario.nome"
                />
            </div>
            <div class="form-group has-feedback {{statusSenha.classe}}">
              <label for="senha">Senha*</label>
              <input
                  type="password"
                  class="form-control"
                  id="senha"
                  placeholder="Informe a senha do Usuário"
                  maxlength="10"
                  required
                  ng-model="usuario.senha"
                  ng-change="validarSenha()"
                />
              <span
                  class="glyphicon form-control-feedback {{statusSenha.icone}}"
                  aria-hidden="true"
                ></span>
              <p class="help-block">{{statusSenha.mensagem}}</p>
            </div>
            <div class="form-group has-feedback {{statusSenha.classe}}">
              <label for="cpf">cpf*</label>
              <input
                  type="password"
                  class="form-control"
                  id="cpf"
                  placeholder="Informe a cpf do Usuário"
                  maxlength="10"
                  required
                  ng-model="usuario.cpf"
                  ng-change="validarcpf()"
                />
              <span
                  class="glyphicon form-control-feedback {{statuscpf.icone}}"
                  aria-hidden="true"
                ></span>
              <p class="help-block">{{statuscpf.mensagem}}</p>
            </div>
            <div class="form-group has-edit">
              <label for="nome"
                  >Para editar os dados, utilizar os campos abaixo:</label>
              <input
                  type="text"
                  class="form-control"
                  placeholder="Altere o nome do usuário"
                  maxlength="20"
                  required
                  ng-model="update.name"
                />
              <input
                  type="password"
                  class="form-control"
                  required
                  ng-model="update.senha"
                  placeholder="Altere a senha do Usuário"
                  maxlength="10"
                  ng-change="validarSenha()"
                />
              <span
                  class="glyphicon form-control-feedback {{statusSenha.icone}}"
                  aria-hidden="true"
                ></span>
              <p class="help-block">{{statusSenha.mensagem}}</p>
            </div>
            <button
                type="submit"
                class="btn btn-primary"
                ng-submit="cadastrar()"
              >
                Cadastrar
              </button>
            <button
                ng-click="salvar()"
                ng-submit="salvar()"
                class="btn btn-primary"
              >
                Editar
              </button>
          </form>
          <hr />
          <h1>Lista de Usuários:</h1>
          <table class="table table-striped" ng-hide="UsuarioController.usuarios == 0">
            <thead>
              <tr>
                <th>Nome</th>
                <th>Senha</th>
                <th>cpf</th>
                <th>Ação</th>
              </tr>
            </thead>
            <tbody>
              <!-- Aqui serão exibidos os dados do usuários cadastrados -->
              <tr ng-repeat="usuario in usuarios">
                <td>{{usuario.nome}}</td>
                <td>{{usuario.senha}}</td>
                <td>{{usuario.cpf}}</td>
                <td>
                  <button
                      class="btn btn-danger btn-xs"
                      ng-click="remover($index)"
                    >
                      Remover
                    </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
  <script
