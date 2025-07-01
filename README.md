{
    "name": "Chatbot de Escuta Empresarial",
    "description": "Fluxo para um chatbot de canal digital de escuta, baseado nas instruções fornecidas.",
    "flow": [
        {
            "id": "welcome_block",
            "type": "send_message",
            "text": "🤖 Olá! Eu sou o canal digital de escuta da nossa empresa. Estou aqui para ouvir você e encaminhar sua manifestação. Como posso te chamar?",
            "next_block": "user_name_input"
        },
        {
            "id": "user_name_input",
            "type": "user_input",
            "variable": "nome",
            "next_block": "main_menu"
        },
        {
            "id": "main_menu",
            "type": "buttons",
            "question": "Sobre o que você quer falar?",
            "options": [
                {
                    "text": "Dúvida",
                    "next_block": "flow_doubt"
                },
                {
                    "text": "Denúncia",
                    "next_block": "flow_complaint"
                },
                {
                    "text": "Reclamação",
                    "next_block": "flow_reclamation"
                },
                {
                    "text": "Agendamento",
                    "next_block": "flow_scheduling"
                },
                {
                    "text": "Informações sobre obras e projetos",
                    "next_block": "flow_info_works"
                },
                {
                    "text": "Elogio",
                    "next_block": "flow_praise"
                },
                {
                    "text": "Outro assunto",
                    "next_block": "flow_other_subject"
                }
            ]
        },
        {
            "id": "flow_reclamation",
            "type": "buttons",
            "question": "Sobre qual tema é a sua reclamação?",
            "options": [
                {
                    "text": "Poeira",
                    "next_block": "reclamation_location"
                },
                {
                    "text": "Ruído",
                    "next_block": "reclamation_location"
                },
                {
                    "text": "Vibração",
                    "next_block": "reclamation_location"
                },
                {
                    "text": "Outros",
                    "next_block": "reclamation_location"
                }
            ]
        },
        {
            "id": "reclamation_location",
            "type": "user_input",
            "question": "📍 Onde isso aconteceu?",
            "variable": "reclamacao_local",
            "next_block": "reclamation_time"
        },
        {
            "id": "reclamation_time",
            "type": "user_input",
            "question": "🕒 Quando aconteceu?",
            "variable": "reclamacao_quando",
            "next_block": "reclamation_description"
        },
        {
            "id": "reclamation_description",
            "type": "user_input",
            "question": "📝 Descreva o que está sentindo ou observando",
            "variable": "reclamacao_descricao",
            "next_block": "reclamation_contact_option"
        },
        {
            "id": "reclamation_contact_option",
            "type": "yes_no",
            "question": "📞 Deseja deixar um contato para resposta?",
            "options": [
                {
                    "text": "Sim",
                    "next_block": "reclamation_contact_input"
                },
                {
                    "text": "Não",
                    "next_block": "reclamation_end"
                }
            ]
        },
        {
            "id": "reclamation_contact_input",
            "type": "user_input",
            "question": "Por favor, informe seu telefone ou e-mail para contato.",
            "variable": "reclamacao_contato",
            "next_block": "reclamation_end"
        },
        {
            "id": "reclamation_end",
            "type": "send_message",
            "text": "📌 Obrigado! Sua manifestação foi registrada e encaminhada à equipe responsável.",
            "next_block": "email_automation"
        },
        {
            "id": "email_automation",
            "type": "automation",
            "action": "send_email",
            "subject": "Nova manifestação registrada",
            "body": "Nome: @nome\nTipo de Manifestação: Reclamação\nLocal: @reclamacao_local\nQuando: @reclamacao_quando\nDescrição: @reclamacao_descricao\nContato: @reclamacao_contato",
            "next_block": "keyword_jump_logic"
        },
        {
            "id": "keyword_jump_logic",
            "type": "logic",
            "action": "keyword_jump_or_conditional_logic",
            "description": "Configurar para responder automaticamente perguntas simples (ex: horário da obra, reunião, poeira)",
            "next_block": "visual_customization"
        },
        {
            "id": "visual_customization",
            "type": "settings",
            "action": "design_customization",
            "description": "Personalizar o visual do bot (nome, cores, imagem de fundo)",
            "next_block": "test_bot"
        },
        {
            "id": "test_bot",
            "type": "action",
            "action_type": "preview_and_test",
            "description": "Testar o bot clicando em Preview e verificar todos os caminhos e coleta de dados."
        }
    ]
}
