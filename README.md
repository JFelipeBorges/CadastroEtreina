# Cadastro e treinamento
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro e Treinamento Revendas</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Estilo para a fonte Inter */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8; /* Light blue-gray background */
        }
        /* Estilo para a scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #e2e8f0;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb {
            background: #94a3b8;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #64748b;
        }
    </style>
</head>
<body class="min-h-screen flex items-center justify-center p-4 bg-gray-100">
    <div class="bg-white p-8 rounded-2xl shadow-xl w-full max-w-5xl">
        <h1 class="text-3xl font-bold text-center text-gray-800 mb-8">Cadastro e Treinamento Revendas</h1>

        <!-- Botões de Navegação -->
        <div class="flex justify-center mb-8 space-x-4">
            <button id="btnCadastro" class="px-6 py-3 bg-blue-600 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-opacity-75 transition duration-300 ease-in-out transform hover:scale-105">
                Cadastro de Revenda
            </button>
            <button id="btnRegistros" class="px-6 py-3 bg-gray-300 text-gray-800 font-semibold rounded-lg shadow-md hover:bg-gray-400 focus:outline-none focus:ring-2 focus:ring-gray-500 focus:ring-opacity-75 transition duration-300 ease-in-out transform hover:scale-105">
                Registros de Revendas
            </button>
        </div>

        <!-- Mensagens de Feedback -->
        <div id="messageBox" class="hidden bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded relative mb-4" role="alert">
            <strong class="font-bold">Sucesso!</strong>
            <span id="messageText" class="block sm:inline"></span>
            <span class="absolute top-0 bottom-0 right-0 px-4 py-3 cursor-pointer" onclick="document.getElementById('messageBox').classList.add('hidden');">
                <svg class="fill-current h-6 w-6 text-green-500" role="button" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><title>Close</title><path d="M14.348 14.849a1.2 1.2 0 0 1-1.697 0L10 11.819l-2.651 3.029a1.2 1.2 0 1 1-1.697-1.697l2.758-3.15-2.759-3.152a1.2 1.2 0 1 1 1.697-1.697L10 8.183l2.651-3.031a1.2 1.2 0 1 1 1.697 1.697l-2.758 3.152 2.758 3.15a1.2 1.2 0 0 1 0 1.698z"/></svg>
            </span>
        </div>
        <div id="errorBox" class="hidden bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative mb-4" role="alert">
            <strong class="font-bold">Erro!</strong>
            <span id="errorText" class="block sm:inline"></span>
            <span class="absolute top-0 bottom-0 right-0 px-4 py-3 cursor-pointer" onclick="document.getElementById('errorBox').classList.add('hidden');">
                <svg class="fill-current h-6 w-6 text-red-500" role="button" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><title>Close</title><path d="M14.348 14.849a1.2 1.2 0 0 1-1.697 0L10 11.819l-2.651 3.029a1.2 1.2 0 1 1-1.697-1.697l2.758-3.15-2.759-3.152a1.2 1.2 0 1 1 1.697-1.697L10 8.183l2.651-3.031a1.2 1.2 0 1 1 1.697 1.697l-2.758 3.152 2.758 3.15a1.2 1.2 0 0 1 0 1.698z"/></svg>
            </span>
        </div>
        <div id="loadingBox" class="hidden bg-blue-100 border border-blue-400 text-blue-700 px-4 py-3 rounded relative mb-4" role="alert">
            <strong class="font-bold">Carregando...</strong>
            <span class="block sm:inline">Por favor, aguarde.</span>
        </div>


        <!-- Seção de Cadastro de Revenda -->
        <div id="cadastroSection" class="p-6 border border-gray-200 rounded-xl bg-gray-50">
            <h2 class="text-2xl font-semibold text-gray-700 mb-6 text-center">Formulário de Cadastro / Atualização</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                <div>
                    <label for="revendaName" class="block text-sm font-medium text-gray-700 mb-1">Nome da Revenda <span class="text-red-500">*</span></label>
                    <input type="text" id="revendaName" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Ex: Revenda Moura Central">
                    <p class="text-xs text-gray-500 mt-1">Use o nome exato para buscar e atualizar um cadastro existente.</p>
                </div>
                <div>
                    <label for="contactName" class="block text-sm font-medium text-gray-700 mb-1">Nome do Contato</label>
                    <input type="text" id="contactName" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Ex: João Silva">
                </div>
                <div>
                    <label for="contactPhone" class="block text-sm font-medium text-gray-700 mb-1">Telefone do Contato</label>
                    <input type="text" id="contactPhone" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Ex: (81) 99999-9999">
                </div>
                <div>
                    <label for="contactEmail" class="block text-sm font-medium text-gray-700 mb-1">E-mail do Contato</label>
                    <input type="email" id="contactEmail" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Ex: contato@revenda.com">
                </div>
                <div>
                    <label for="cnpj" class="block text-sm font-medium text-gray-700 mb-1">CNPJ</label>
                    <input type="text" id="cnpj" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Ex: XX.XXX.XXX/XXXX-XX">
                </div>
                <div>
                    <label for="distributor" class="block text-sm font-medium text-gray-700 mb-1">Distribuidor/Unidade Responsável</label>
                    <select id="distributor" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                        <option value="">Selecione um distribuidor</option>
                        <option value="Alagoana Filial Arapiraca">Alagoana Filial Arapiraca</option>
                        <option value="Alagoana Matriz">Alagoana Matriz</option>
                        <option value="Anápolis Matriz">Anápolis Matriz</option>
                        <option value="Anhanguera">Anhanguera</option>
                        <option value="Autobate Matriz">Autobate Matriz</option>
                        <option value="Avic Filial Guarapuava">Avic Filial Guarapuava</option>
                        <option value="Avic Matriz">Avic Matriz</option>
                        <option value="Bandeirantes Matriz">Bandeirantes Matriz</option>
                        <option value="Batermol Matriz">Batermol Matriz</option>
                        <option value="Bauru Matriz">Bauru Matriz</option>
                        <option value="Belo Jardim Matriz">Belo Jardim Matriz</option>
                        <option value="Blumenau Matriz">Blumenau Matriz</option>
                        <option value="Bonfim Matriz">Bonfim Matriz</option>
                        <option value="Brasiliense Matriz">Brasiliense Matriz</option>
                        <option value="Campo Grande Filial Dourados">Campo Grande Filial Dourados</option>
                        <option value="Campo Grande Matriz">Campo Grande Matriz</option>
                        <option value="Campo Limpo">Campo Limpo</option>
                        <option value="Campos Gerais">Campos Gerais</option>
                        <option value="Cariri Matriz">Cariri Matriz</option>
                        <option value="Cascavel Matriz">Cascavel Matriz</option>
                        <option value="Catarinense Matriz">Catarinense Matriz</option>
                        <option value="Caxias">Caxias</option>
                        <option value="Chapecoense Filial Lages">Chapecoense Filial Lages</option>
                        <option value="Chapecoense Matriz">Chapecoense Matriz</option>
                        <option value="Codiba Matriz">Codiba Matriz</option>
                        <option value="Comal Filial Cachoeiro do Itapemirim">Comal Filial Cachoeiro do Itapemirim</option>
                        <option value="Comal Filial Linhares">Comal Filial Linhares</option>
                        <option value="Comal Matriz">Comal Matriz</option>
                        <option value="Combat Filial Juazeiro do Norte">Combat Filial Juazeiro do Norte</option>
                        <option value="Combat Matriz">Combat Matriz</option>
                        <option value="Cominas Matriz">Cominas Matriz</option>
                        <option value="Conorte Filial Governador Valadares">Conorte Filial Governador Valadares</option>
                        <option value="Conorte Matriz">Conorte Matriz</option>
                        <option value="Criciúma">Criciúma</option>
                        <option value="Dinil Filial Campos">Dinil Filial Campos</option>
                        <option value="Dinil Matriz">Dinil Matriz</option>
                        <option value="Dirpal Matriz">Dirpal Matriz</option>
                        <option value="Disbac Matriz">Disbac Matriz</option>
                        <option value="Disbate Matriz">Disbate Matriz</option>
                        <option value="Dismal Matriz">Dismal Matriz</option>
                        <option value="Fluminense Filial Campo Grande">Fluminense Filial Campo Grande</option>
                        <option value="Fluminense Matriz">Fluminense Matriz</option>
                        <option value="Fortaleza Matriz">Fortaleza Matriz</option>
                        <option value="Godal Matriz">Godal Matriz</option>
                        <option value="Iguatu">Iguatu</option>
                        <option value="Imperatriz">Imperatriz</option>
                        <option value="Interbahia Filial Barreiras">Interbahia Filial Barreiras</option>
                        <option value="Interbahia Filial Vitória da Conquista">Interbahia Filial Vitória da Conquista</option>
                        <option value="Interbahia Matriz">Interbahia Matriz</option>
                        <option value="Itabuna">Itabuna</option>
                        <option value="Itaquera">Itaquera</option>
                        <option value="Joinville">Joinville</option>
                        <option value="Juiz de Fora Matriz">Juiz de Fora Matriz</option>
                        <option value="Macapá Matriz">Macapá Matriz</option>
                        <option value="Marabá">Marabá</option>
                        <option value="Norte Filial Boa Vista">Norte Filial Boa Vista</option>
                        <option value="Norte Matriz">Norte Matriz</option>
                        <option value="Nova Iguaçu Matriz">Nova Iguaçu Matriz</option>
                        <option value="Osasco">Osasco</option>
                        <option value="Palácio Matriz">Palácio Matriz</option>
                        <option value="Paraense Matriz">Paraense Matriz</option>
                        <option value="Paraíba Matriz">Paraíba Matriz</option>
                        <option value="Patos de Minas Matriz">Patos de Minas Matriz</option>
                        <option value="Paulista Matriz">Paulista Matriz</option>
                        <option value="Piauiense Matriz">Piauiense Matriz</option>
                        <option value="Poços de Caldas">Poços de Caldas</option>
                        <option value="Porto Velho Matriz">Porto Velho Matriz</option>
                        <option value="Presidente Prudente">Presidente Prudente</option>
                        <option value="Rodmaster Filial Pelotas">Rodmaster Filial Pelotas</option>
                        <option value="Rodmaster Matriz">Rodmaster Matriz</option>
                        <option value="Santa Maria Filial Passo Fundo">Santa Maria Filial Passo Fundo</option>
                        <option value="Santa Maria Matriz">Santa Maria Matriz</option>
                        <option value="Santarém">Santarém</option>
                        <option value="Santos">Santos</option>
                        <option value="São Carlos">São Carlos</option>
                        <option value="Serve Vale Filial Taubaté">Serve Vale Filial Taubaté</option>
                        <option value="Serve Vale Matriz">Serve Vale Matriz</option>
                        <option value="Sinop">Sinop</option>
                        <option value="Sobral">Sobral</option>
                        <option value="Sorocaba">Sorocaba</option>
                        <option value="Tocantins Matriz">Tocantins Matriz</option>
                        <option value="Triângulo Matriz">Triângulo Matriz</option>
                        <option value="União Matriz">União Matriz</option>
                        <option value="Vila Bela">Vila Bela</option>
                        <option value="Volta Redonda Matriz">Volta Redonda Matriz</option>
                    </select>
                </div>
                <div>
                    <label for="registrationDate" class="block text-sm font-medium text-gray-700 mb-1">Data do Cadastro</label>
                    <input type="date" id="registrationDate" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                </div>
                <div>
                    <label for="sdmId" class="block text-sm font-medium text-gray-700 mb-1">ID da Solicitação SDM</label>
                    <input type="text" id="sdmId" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Ex: SDM12345">
                </div>
                <div>
                    <label for="analystName" class="block text-sm font-medium text-gray-700 mb-1">Nome do Analista</label>
                    <input type="text" id="analystName" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Ex: Ana Souza">
                </div>
                <div class="col-span-1 md:col-span-2">
                    <label for="notes" class="block text-sm font-medium text-gray-700 mb-1">Observações</label>
                    <textarea id="notes" rows="3" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm" placeholder="Informações adicionais sobre a revenda..."></textarea>
                </div>

                <div class="col-span-1 md:col-span-2 grid grid-cols-1 md:grid-cols-3 gap-6">
                    <div class="flex items-center">
                        <input id="trainingLinkSent" type="checkbox" class="h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                        <label for="trainingLinkSent" class="ml-2 block text-sm font-medium text-gray-700">Link para Agendamento Enviado</label>
                    </div>
                    <div>
                        <label for="trainingScheduledDate" class="block text-sm font-medium text-gray-700 mb-1">Data do Agendamento</label>
                        <input type="date" id="trainingScheduledDate" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                    </div>
                    <div class="flex items-center">
                        <input id="trainingCompleted" type="checkbox" class="h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                        <label for="trainingCompleted" class="ml-2 block text-sm font-medium text-gray-700">Treinamento Realizado</label>
                    </div>
                    <div class="flex items-center">
                        <input id="activated" type="checkbox" class="h-4 w-4 text-blue-600 border-gray-300 rounded focus:ring-blue-500">
                        <label for="activated" class="ml-2 block text-sm font-medium text-gray-700">Ativação Realizada</label>
                    </div>
                    <div>
                        <label for="activationDate" class="block text-sm font-medium text-gray-700 mb-1">Data da Ativação</label>
                        <input type="date" id="activationDate" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm">
                    </div>
                </div>
            </div>

            <div class="flex justify-center space-x-4">
                <button id="saveBtn" class="px-6 py-3 bg-green-600 text-white font-semibold rounded-lg shadow-md hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-75 transition duration-300 ease-in-out transform hover:scale-105">
                    Salvar / Atualizar Cadastro
                </button>
                <button id="clearBtn" class="px-6 py-3 bg-red-600 text-white font-semibold rounded-lg shadow-md hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-opacity-75 transition duration-300 ease-in-out transform hover:scale-105">
                    Limpar Campos
                </button>
            </div>
        </div>

        <!-- Seção de Registros de Revendas -->
        <div id="registrosSection" class="p-6 border border-gray-200 rounded-xl bg-gray-50 hidden">
            <h2 class="text-2xl font-semibold text-gray-700 mb-6 text-center">Registros de Revendas</h2>
            <div class="flex items-center justify-between mb-4">
                <p class="text-sm text-gray-600">ID do Usuário Logado: <span id="currentUserId" class="font-bold text-blue-700 break-all">Carregando...</span></p>
                <p class="text-sm text-gray-600">Total de Revendas: <span id="totalRevendas" class="font-bold text-blue-700">0</span></p>
                <button id="exportCsvBtn" class="px-4 py-2 bg-purple-600 text-white font-semibold rounded-lg shadow-md hover:bg-purple-700 focus:outline-none focus:ring-2 focus:ring-purple-500 focus:ring-opacity-75 transition duration-300 ease-in-out transform hover:scale-105">
                    Exportar para Planilha (CSV)
                </button>
            </div>
            <div class="overflow-x-auto rounded-lg shadow-md border border-gray-200">
                <table class="min-w-full divide-y divide-gray-200">
                    <thead class="bg-gray-100">
                        <tr>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Nome da Revenda</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Contato</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Telefone</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">E-mail</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">CNPJ</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Distribuidor</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Data Cad.</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">ID SDM</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Analista</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Link Enviado</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Data Agend.</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Trein. Realizado</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Ativação Realizada</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Data Ativ.</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Observações</th>
                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Ações</th>
                        </tr>
                    </thead>
                    <tbody id="registrosTableBody" class="bg-white divide-y divide-gray-200">
                        <!-- Os registros serão inseridos aqui pelo JavaScript -->
                    </tbody>
                </table>
            </div>
            <p class="text-sm text-gray-500 mt-4 text-center">Os registros nesta tabela não podem ser editados diretamente. Use a aba "Cadastro de Revenda" para atualizá-los.</p>
        </div>
    </div>

    <!-- Firebase SDKs -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js";
        import { getAuth, signInAnonymously, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-auth.js";
        import { getFirestore, collection, query, onSnapshot, addDoc, updateDoc, doc, where, getDocs, deleteDoc } from "https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore.js";

        // ATENÇÃO: As variáveis __app_id, __firebase_config e __initial_auth_token são fornecidas pelo ambiente Canvas.
        // Para usar este aplicativo fora do Canvas (ex: GitHub Pages), você precisará fornecer sua própria configuração Firebase.
        // Substitua os valores abaixo pela sua configuração real do projeto Firebase.

        // Obtenha sua configuração Firebase em: Console do Firebase -> Configurações do Projeto -> Seus aplicativos -> Adicione um aplicativo web
        const firebaseConfig = {
            apiKey: "COLE_SUA_API_KEY_AQUI", // Ex: "AIzaSyC..."
            authDomain: "SEU_PROJETO.firebaseapp.com", // Ex: "meu-projeto-123.firebaseapp.com"
            projectId: "SEU_PROJECT_ID", // Ex: "meu-projeto-123"
            storageBucket: "SEU_STORAGE_BUCKET.appspot.com", // Ex: "meu-projeto-123.appspot.com"
            messagingSenderId: "SEU_MESSAGING_SENDER_ID", // Ex: "1234567890"
            appId: "SEU_APP_ID" // Ex: "1:234567890:web:abcdef1234567890abcdef"
        };

        // Use o projectId como appId para o caminho do Firestore, ou defina um manualmente.
        // Certifique-se de que isso corresponde ao seu path nas regras do Firestore: /artifacts/{appId}/public/data/...
        const appId = firebaseConfig.projectId; // Recomenda-se usar o Project ID para consistência.

        // Elementos UI
        const btnCadastro = document.getElementById('btnCadastro');
        const btnRegistros = document.getElementById('btnRegistros');
        const cadastroSection = document.getElementById('cadastroSection');
        const registrosSection = document.getElementById('registrosSection');

        const revendaNameInput = document.getElementById('revendaName');
        const contactNameInput = document.getElementById('contactName');
        const contactPhoneInput = document.getElementById('contactPhone');
        const contactEmailInput = document.getElementById('contactEmail');
        const cnpjInput = document.getElementById('cnpj');
        const distributorInput = document.getElementById('distributor'); // Agora é um select
        const registrationDateInput = document.getElementById('registrationDate');
        const sdmIdInput = document.getElementById('sdmId');
        const analystNameInput = document.getElementById('analystName');
        const notesInput = document.getElementById('notes');
        const trainingLinkSentCheckbox = document.getElementById('trainingLinkSent');
        const trainingScheduledDateInput = document.getElementById('trainingScheduledDate');
        const trainingCompletedCheckbox = document.getElementById('trainingCompleted');
        const activationDateInput = document.getElementById('activationDate');
        const activatedCheckbox = document.getElementById('activated');

        const saveBtn = document.getElementById('saveBtn');
        const clearBtn = document.getElementById('clearBtn');
        const exportCsvBtn = document.getElementById('exportCsvBtn');
        const registrosTableBody = document.getElementById('registrosTableBody');
        const messageBox = document.getElementById('messageBox');
        const messageText = document.getElementById('messageText');
        const errorBox = document.getElementById('errorBox');
        const errorText = document.getElementById('errorText');
        const loadingBox = document.getElementById('loadingBox');
        const currentUserIdSpan = document.getElementById('currentUserId');
        const totalRevendasSpan = document.getElementById('totalRevendas');

        let db;
        let auth;
        let userId = 'anon'; // Default user ID
        let allRevendasData = []; // Para armazenar todos os dados para exportação

        // --- Funções de UI ---

        /**
         * Exibe uma mensagem de sucesso na interface do usuário.
         * @param {string} message - A mensagem a ser exibida.
         */
        function showMessage(message) {
            messageText.textContent = message;
            messageBox.classList.remove('hidden');
            errorBox.classList.add('hidden'); // Esconde erro se houver
            setTimeout(() => messageBox.classList.add('hidden'), 5000); // Esconde após 5 segundos
        }

        /**
         * Exibe uma mensagem de erro na interface do usuário.
         * @param {string} message - A mensagem de erro a ser exibida.
         */
        function showError(message) {
            errorText.textContent = message;
            errorBox.classList.remove('hidden');
            messageBox.classList.add('hidden'); // Esconde sucesso se houver
            setTimeout(() => errorBox.classList.add('hidden'), 5000); // Esconde após 5 segundos
        }

        /**
         * Exibe ou esconde o indicador de carregamento.
         * @param {boolean} show - Verdadeiro para mostrar, falso para esconder.
         */
        function toggleLoading(show) {
            if (show) {
                loadingBox.classList.remove('hidden');
            } else {
                loadingBox.classList.add('hidden');
            }
        }

        /**
         * Limpa todos os campos do formulário de cadastro.
         */
        function clearForm() {
            revendaNameInput.value = '';
            contactNameInput.value = '';
            contactPhoneInput.value = '';
            contactEmailInput.value = '';
            cnpjInput.value = '';
            distributorInput.value = ''; // Limpa o select
            registrationDateInput.value = '';
            sdmIdInput.value = '';
            analystNameInput.value = '';
            notesInput.value = '';
            trainingLinkSentCheckbox.checked = false;
            trainingScheduledDateInput.value = '';
            trainingCompletedCheckbox.checked = false;
            activationDateInput.value = '';
            activatedCheckbox.checked = false;
        }

        /**
         * Alterna a visibilidade das seções de Cadastro e Registros.
         * @param {string} sectionId - O ID da seção a ser mostrada ('cadastroSection' ou 'registrosSection').
         */
        function showSection(sectionId) {
            if (sectionId === 'cadastroSection') {
                cadastroSection.classList.remove('hidden');
                registrosSection.classList.add('hidden');
                btnCadastro.classList.remove('bg-gray-300', 'text-gray-800');
                btnCadastro.classList.add('bg-blue-600', 'text-white');
                btnRegistros.classList.remove('bg-blue-600', 'text-white');
                btnRegistros.classList.add('bg-gray-300', 'text-gray-800');
            } else {
                cadastroSection.classList.add('hidden');
                registrosSection.classList.remove('hidden');
                btnRegistros.classList.remove('bg-gray-300', 'text-gray-800');
                btnRegistros.classList.add('bg-blue-600', 'text-white');
                btnCadastro.classList.remove('bg-blue-600', 'text-white');
                btnCadastro.classList.add('bg-gray-300', 'text-gray-800');
            }
        }

        // --- Funções de Firebase ---

        /**
         * Inicializa o Firebase e a autenticação.
         */
        async function initializeFirebase() {
            try {
                toggleLoading(true);
                const app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);

                // Para hospedagem externa, usaremos autenticação anônima,
                // que é suficiente para as regras de segurança padrão (request.auth != null)
                // e não requer um token de autenticação inicial.
                await signInAnonymously(auth);

                // Observa mudanças no estado de autenticação
                onAuthStateChanged(auth, (user) => {
                    if (user) {
                        userId = user.uid;
                        currentUserIdSpan.textContent = userId;
                        // Inicia o listener de Firestore apenas após a autenticação
                        setupFirestoreListener();
                    } else {
                        // Caso a autenticação anônima falhe ou não esteja pronta, um userId temporário.
                        // Em um app real, você pode querer forçar um login ou mostrar um erro mais claro.
                        userId = crypto.randomUUID(); // Gera um ID único aleatório
                        currentUserIdSpan.textContent = `ID Temporário: ${userId.substring(0, 8)}...`;
                        console.warn("Usuário não autenticado. Usando ID temporário. Operações Firestore podem ser restritas.");
                        // Tentar configurar o listener mesmo com ID temporário, mas esteja ciente das regras de segurança.
                        setupFirestoreListener();
                    }
                    toggleLoading(false);
                });

            } catch (e) {
                console.error("Erro ao inicializar Firebase ou autenticar:", e);
                showError("Erro ao iniciar o aplicativo. Por favor, verifique sua configuração Firebase e tente novamente.");
                toggleLoading(false);
            }
        }

        /**
         * Configura o listener para a coleção de revendas no Firestore.
         * Atualiza a tabela de registros em tempo real.
         */
        function setupFirestoreListener() {
            if (!db) {
                console.error("Firestore não inicializado. O listener não pode ser configurado.");
                return;
            }

            // O caminho da coleção é público dentro do appId para colaboração
            // Certifique-se que o appId aqui corresponde ao 'projectId' ou ao ID que você definiu.
            const collectionPath = `artifacts/${appId}/public/data/resellers`;
            const q = collection(db, collectionPath);

            onSnapshot(q, (snapshot) => {
                registrosTableBody.innerHTML = ''; // Limpa a tabela antes de preencher
                allRevendasData = []; // Limpa os dados para exportação
                let total = 0;
                snapshot.forEach((docData) => {
                    total++;
                    const data = docData.data();
                    allRevendasData.push(data); // Adiciona para a lista de exportação

                    const row = registrosTableBody.insertRow();
                    row.classList.add('hover:bg-gray-50');

                    // Função auxiliar para formatar datas
                    const formatDate = (timestamp) => {
                        if (!timestamp) return '';
                        const date = timestamp.toDate ? timestamp.toDate() : new Date(timestamp);
                        return date.toLocaleDateString('pt-BR');
                    };

                    // Adiciona as células com os dados da revenda
                    row.insertCell().textContent = data.revendaName || '';
                    row.insertCell().textContent = data.contactName || '';
                    row.insertCell().textContent = data.contactPhone || '';
                    row.insertCell().textContent = data.contactEmail || '';
                    row.insertCell().textContent = data.cnpj || '';
                    row.insertCell().textContent = data.distributor || '';
                    row.insertCell().textContent = formatDate(data.registrationDate);
                    row.insertCell().textContent = data.sdmId || '';
                    row.insertCell().textContent = data.analystName || '';
                    row.insertCell().innerHTML = data.trainingLinkSent ? '<span class="text-green-500 font-bold">&#10003; Sim</span>' : '<span class="text-red-500">&#10007; Não</span>';
                    row.insertCell().textContent = formatDate(data.trainingScheduledDate);
                    row.insertCell().innerHTML = data.trainingCompleted ? '<span class="text-green-500 font-bold">&#10003; Sim</span>' : '<span class="text-red-500">&#10007; Não</span>';
                    row.insertCell().innerHTML = data.activated ? '<span class="text-green-500 font-bold">&#10003; Sim</span>' : '<span class="text-red-500">&#10007; Não</span>';
                    row.insertCell().textContent = formatDate(data.activationDate);
                    row.insertCell().textContent = data.notes || '';

                    // Botões de Ação na tabela (Editar e Excluir)
                    const actionCell = row.insertCell();
                    actionCell.classList.add('px-6', 'py-4', 'whitespace-nowrap', 'text-right', 'text-sm', 'font-medium');

                    const editBtn = document.createElement('button');
                    editBtn.textContent = 'Editar';
                    editBtn.classList.add('text-blue-600', 'hover:text-blue-900', 'mr-2', 'px-2', 'py-1', 'rounded', 'border', 'border-blue-600', 'hover:bg-blue-50');
                    editBtn.onclick = () => loadRevendaForEdit(docData.id, data);
                    actionCell.appendChild(editBtn);

                    const deleteBtn = document.createElement('button');
                    deleteBtn.textContent = 'Excluir';
                    deleteBtn.classList.add('text-red-600', 'hover:text-red-900', 'px-2', 'py-1', 'rounded', 'border', 'border-red-600', 'hover:bg-red-50');
                    deleteBtn.onclick = () => confirmDeleteRevenda(docData.id, data.revendaName);
                    actionCell.appendChild(deleteBtn);
                });
                totalRevendasSpan.textContent = total;
            }, (error) => {
                console.error("Erro ao carregar registros de revendas:", error);
                showError("Erro ao carregar os registros. Tente recarregar a página.");
            });
        }

        /**
         * Carrega os dados de uma revenda para edição no formulário de cadastro.
         * @param {string} id - O ID do documento da revenda.
         * @param {object} data - Os dados da revenda.
         */
        function loadRevendaForEdit(id, data) {
            showSection('cadastroSection'); // Volta para a seção de cadastro

            revendaNameInput.value = data.revendaName || '';
            contactNameInput.value = data.contactName || '';
            contactPhoneInput.value = data.contactPhone || '';
            contactEmailInput.value = data.contactEmail || '';
            cnpjInput.value = data.cnpj || '';
            distributorInput.value = data.distributor || ''; // Preenche o select
            registrationDateInput.value = data.registrationDate ? (data.registrationDate.toDate ? data.registrationDate.toDate().toISOString().split('T')[0] : new Date(data.registrationDate).toISOString().split('T')[0]) : '';
            sdmIdInput.value = data.sdmId || '';
            analystNameInput.value = data.analystName || '';
            notesInput.value = data.notes || '';
            trainingLinkSentCheckbox.checked = data.trainingLinkSent || false;
            trainingScheduledDateInput.value = data.trainingScheduledDate ? (data.trainingScheduledDate.toDate ? data.trainingScheduledDate.toDate().toISOString().split('T')[0] : new Date(data.trainingScheduledDate).toISOString().split('T')[0]) : '';
            trainingCompletedCheckbox.checked = data.trainingCompleted || false;
            activatedCheckbox.checked = data.activated || false;
            activationDateInput.value = data.activationDate ? (data.activationDate.toDate ? data.activationDate.toDate().toISOString().split('T')[0] : new Date(data.activationDate).toISOString().split('T')[0]) : '';

            // Armazena o ID do documento atual para uso na atualização
            revendaNameInput.dataset.docId = id;
            showMessage(`Dados de '${data.revendaName}' carregados para edição.`);
        }

        /**
         * Confirma a exclusão de uma revenda.
         * @param {string} id - O ID do documento da revenda.
         * @param {string} name - O nome da revenda.
         */
        function confirmDeleteRevenda(id, name) {
            if (window.confirm(`Tem certeza que deseja excluir o cadastro da revenda '${name}'?`)) {
                deleteRevenda(id);
            }
        }

        /**
         * Exclui um documento de revenda do Firestore.
         * @param {string} docId - O ID do documento a ser excluído.
         */
        async function deleteRevenda(docId) {
            if (!db) {
                showError("Firestore não inicializado.");
                return;
            }
            toggleLoading(true);
            try {
                const docRef = doc(db, `artifacts/${appId}/public/data/resellers`, docId);
                await deleteDoc(docRef);
                showMessage("Revenda excluída com sucesso!");
            } catch (e) {
                console.error("Erro ao excluir revenda:", e);
                showError("Erro ao excluir revenda. Tente novamente.");
            } finally {
                toggleLoading(false);
            }
        }


        /**
         * Salva ou atualiza um registro de revenda no Firestore.
         */
        async function saveRevenda() {
            if (!db) {
                showError("Firestore não inicializado.");
                return;
            }

            const revendaName = revendaNameInput.value.trim();
            if (!revendaName) {
                showError("O 'Nome da Revenda' é obrigatório.");
                return;
            }

            toggleLoading(true);
            try {
                // Prepara os dados para salvar/atualizar
                const revendaData = {
                    revendaName: revendaName,
                    contactName: contactNameInput.value.trim(),
                    contactPhone: contactPhoneInput.value.trim(),
                    contactEmail: contactEmailInput.value.trim(),
                    cnpj: cnpjInput.value.trim(),
                    distributor: distributorInput.value, // Pega o valor selecionado do select
                    registrationDate: registrationDateInput.value ? new Date(registrationDateInput.value) : null,
                    sdmId: sdmIdInput.value.trim(),
                    analystName: analystNameInput.value.trim(),
                    notes: notesInput.value.trim(),
                    trainingLinkSent: trainingLinkSentCheckbox.checked,
                    trainingScheduledDate: trainingScheduledDateInput.value ? new Date(trainingScheduledDateInput.value) : null,
                    trainingCompleted: trainingCompletedCheckbox.checked,
                    activated: activatedCheckbox.checked,
                    activationDate: activationDateInput.value ? new Date(activationDateInput.value) : null,
                    updatedBy: userId, // Quem fez a última atualização
                    updatedAt: new Date(),
                };

                // Verifica se já existe uma revenda com o mesmo nome para atualização
                const q = query(collection(db, `artifacts/${appId}/public/data/resellers`), where("revendaName", "==", revendaName));
                const querySnapshot = await getDocs(q);

                if (!querySnapshot.empty) {
                    // Revenda encontrada, atualiza o primeiro documento correspondente
                    querySnapshot.forEach(async (docSnap) => {
                        await updateDoc(doc(db, `artifacts/${appId}/public/data/resellers`, docSnap.id), revendaData);
                        showMessage(`Cadastro de '${revendaName}' atualizado com sucesso!`);
                    });
                } else {
                    // Revenda não encontrada, adiciona um novo documento
                    revendaData.createdAt = new Date(); // Apenas para novos cadastros
                    revendaData.createdBy = userId;
                    await addDoc(collection(db, `artifacts/${appId}/public/data/resellers`), revendaData);
                    showMessage(`Revenda '${revendaName}' cadastrada com sucesso!`);
                }

                clearForm(); // Limpa o formulário após o envio
            } catch (e) {
                console.error("Erro ao salvar/atualizar revenda:", e);
                showError("Erro ao salvar/atualizar revenda. Verifique sua conexão e tente novamente.");
            } finally {
                toggleLoading(false);
            }
        }

        /**
         * Exporta os dados da tabela para um arquivo CSV.
         */
        function exportToCsv() {
            if (allRevendasData.length === 0) {
                showError("Não há dados para exportar.");
                return;
            }

            const headers = [
                "Nome da Revenda", "Contato", "Telefone", "E-mail", "CNPJ", "Distribuidor/Unidade Responsável",
                "Data do Cadastro", "ID da Solicitação SDM", "Nome do Analista", "Link para Agendamento Enviado",
                "Data do Agendamento", "Treinamento Realizado", "Ativação Realizada", "Data da Ativação",
                "Observações", "Criado por", "Criado em", "Atualizado por", "Atualizado em"
            ];

            // Função para formatar o valor para CSV
            const escapeCsv = (value) => {
                if (value === null || value === undefined) return '';
                let stringValue = String(value);
                if (stringValue.includes(',') || stringValue.includes('"') || stringValue.includes('\n') || stringValue.includes('\r')) {
                    return `"${stringValue.replace(/"/g, '""')}"`;
                }
                return stringValue;
            };

            const rows = allRevendasData.map(data => {
                const formatDateForCsv = (timestamp) => {
                    if (!timestamp) return '';
                    const date = timestamp.toDate ? timestamp.toDate() : new Date(timestamp);
                    return date.toLocaleDateString('pt-BR'); // Formato dd/mm/aaaa
                };

                return [
                    escapeCsv(data.revendaName),
                    escapeCsv(data.contactName),
                    escapeCsv(data.contactPhone),
                    escapeCsv(data.contactEmail),
                    escapeCsv(data.cnpj),
                    escapeCsv(data.distributor),
                    escapeCsv(formatDateForCsv(data.registrationDate)),
                    escapeCsv(data.sdmId),
                    escapeCsv(data.analystName),
                    escapeCsv(data.trainingLinkSent ? 'Sim' : 'Não'),
                    escapeCsv(formatDateForCsv(data.trainingScheduledDate)),
                    escapeCsv(data.trainingCompleted ? 'Sim' : 'Não'),
                    escapeCsv(data.activated ? 'Sim' : 'Não'),
                    escapeCsv(formatDateForCsv(data.activationDate)),
                    escapeCsv(data.notes),
                    escapeCsv(data.createdBy),
                    escapeCsv(formatDateForCsv(data.createdAt)),
                    escapeCsv(data.updatedBy),
                    escapeCsv(formatDateForCsv(data.updatedAt))
                ].join(',');
            });

            const csvContent = [headers.join(','), ...rows].join('\n');
            const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.setAttribute('download', 'registros_revendas.csv');
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            showMessage("Dados exportados para registros_revendas.csv!");
        }

        // --- Event Listeners ---

        window.onload = initializeFirebase; // Inicializa Firebase quando a página carrega

        btnCadastro.addEventListener('click', () => showSection('cadastroSection'));
        btnRegistros.addEventListener('click', () => showSection('registrosSection'));
        saveBtn.addEventListener('click', saveRevenda);
        clearBtn.addEventListener('click', clearForm);
        exportCsvBtn.addEventListener('click', exportToCsv);

        // Define a seção inicial
        showSection('cadastroSection');
    </script>
</body>
</html>
