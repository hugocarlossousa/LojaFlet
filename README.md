from kivy.uix.gridlayout import product
import flet as ft 

def main(page: ft.Page):
    page.title = 'Loja Test - Flet'
    page.bgcolor= ft.colors.BLACK
    page.window_width= 800
    page.window_height= 730
    
    def change_main_image(e):
        for elem in options.controls:
            if elem == e.control:
                elem.opacity = 1
                main_image.src = elem.image_src
            else:
                elem.opacity = 0.5
                
        main_image.update()
        options.update()
    
    product_images = ft.Container(
        col={'xs':12, 'sm':6},
        bgcolor=ft.colors.WHITE,
        padding=ft.padding.all(30),
        aspect_ratio=9/16,
        content= ft.Column(
            alignment=ft.MainAxisAlignment.SPACE_BETWEEN,
            controls=[
                main_image := ft.Image(
                    src='https://bouncewear.com/cdn/shop/products/AT0515-063-PHSFH001.jpg?crop=center&height=1750&v=1650532242&width=1750'
                ),
                
                options := ft.Row(
                    alignment= ft.MainAxisAlignment.CENTER,
                    controls=[
                        ft.Container(
                            image_src='https://bouncewear.com/cdn/shop/products/AT0515-063-PHSFH001.jpg?crop=center&height=1750&v=1650532242&width=1750',
                            width=70,
                            height=70,
                            opacity=1,
                            on_click=change_main_image,                        
                        ),
                        ft.Container(
                            image_src='https://bouncewear.com/cdn/shop/products/AT0515-063-PHSBH001.jpg?crop=center&height=1750&v=1650532242&width=1750',
                            width=70,
                            height=70,
                            opacity=0.5,
                            on_click=change_main_image,                        
                        ),
                        ft.Container(
                            image_src='https://images.footballfanatics.com/logo-gear/nba-primary-colour-wordmark-t-shirt-mens_ss4_p-12088851+pv-1+u-19hgl1vxyz4uy2njc89f+v-319f7318a25b4e309be5d9d0b6d2ee11.jpg?_hv=2&w=900',
                            width=70,
                            height=70,
                            opacity=0.5,
                            on_click=change_main_image,                        
                        ),
                        ft.Container(
                            image_src='https://images.footballfanatics.com/logo-gear/nba-primary-colour-wordmark-t-shirt-mens_ss4_p-12088851+pv-2+u-19hgl1vxyz4uy2njc89f+v-3c95cd3b700d48479cba7158fd81920a.jpg?_hv=2&w=900',
                            width=70,
                            height=70,
                            opacity=0.5,
                            on_click=change_main_image,                        
                        ),
                    ]
                )
            ]
        )
    )
    
    product_datails = ft.Container(
        col={'xs':12, 'sm':6},
        padding=ft.padding.all(30),
        bgcolor=ft.colors.BLACK87,
        aspect_ratio=9/16,
        content=ft.Column(
            controls=[
                ft.Text(value='ROUPAS ESPORTES',
                        color=ft.colors.AMBER,
                        weight=ft.FontWeight.BOLD
                        ),
                
                ft.Text(value='T-Shirt Nike NBA',
                        color=ft.colors.WHITE,
                        weight=ft.FontWeight.BOLD,
                        size=25
                        ),
                ft.Text(value='NBA legue Squad',color=ft.colors.GREY,italic=True),
                
                ft.ResponsiveRow(
                    columns=12,
                    controls=[
                        ft.Text(
                            col={'xs':12, 'sm':6},
                            value='R$ 149.00',
                            color=ft.colors.WHITE,
                            size=20,                            
                        ),
                        ft.Row(
                            col={'xs':12, 'sm':6},
                            controls=[
                                ft.Icon(
                                    name=ft.icons.STAR,
                                    color=ft.colors.AMBER if _ < 4.4 else ft.colors.WHITE,
                                )for _ in range(5)
                                
                            ]
                        )
                    ]
                ),
                
                ft.Tabs(
                    selected_index=0,
                    height=150,
                    indicator_color=ft.colors.AMBER,
                    label_color=ft.colors.AMBER,
                    unselected_label_color=ft.colors.GREY,
                    tabs=[
                        ft.Tab(
                            text='Descrição',
                            content=ft.Container(
                                padding=ft.padding.all(0.5),
                                content=ft.Text(
                                    value= 'Uma peça clássica que se reinventa com o estilo do basquete. Perfeito para um look casual se você ainda quer mostrar qual time é o seu favorito.',
                                    color=ft.colors.GREY,
                                )
                            )
                        ),
                        
                        ft.Tab(
                            text='Especificações',
                            content=ft.Container(
                                padding=ft.padding.all(0.5),
                                content=ft.Text(
                                    value= 'Camiseta lisa, com excelente acabamento de costura e malha de primeirissima qualidade, com fio 30/1 compactada, diversas cores e tamanhos',
                                    color=ft.colors.GREY,
                                )
                            ) 
                        )               
                    ]
                ),
                ft.ResponsiveRow(
                    columns=12,
                    controls=[
                        ft.Dropdown(
                            col=6,
                            label='Tamanho',
                            label_style=ft.TextStyle(color=ft.colors.WHITE),
                            border_color=ft.colors.GREY,
                            border_width=0.5,
                            options=[
                                ft.dropdown.Option(text='P'),
                                ft.dropdown.Option(text='M'),
                                ft.dropdown.Option(text='G'),
                                ft.dropdown.Option(text='GG'),
                                ft.dropdown.Option(text='2GG'),
                                ft.dropdown.Option(text='3GG'),
                                ft.dropdown.Option(text='4GG'),
                            ]
                        ),
                                               
                       ft.Dropdown(
                          col=6,
                            label='Quantidade',
                            label_style=ft.TextStyle(color=ft.colors.WHITE),
                            border_color=ft.colors.GREY,
                            border_width=0.5,
                            options=[
                                ft.dropdown.Option(text= f'{num} unid.') for num in range(1,11)
                                
                            ]
                        ),
                    ]
                ),
                ft.Container(expand=True),
                ft.ElevatedButton(
                    width=900,
                    text='Adicionar a lista de desejos',
                    style=ft.ButtonStyle(
                        padding=ft.padding.all(20),
                        side={
                            ft.MaterialState.DEFAULT: ft.BorderSide(width=2, color=ft.colors.WHITE)
                        },
                        bgcolor={
                            ft.MaterialState.HOVERED: ft.colors.WHITE
                        },
                        color={
                            ft.MaterialState.DEFAULT: ft.colors.WHITE,
                            ft.MaterialState.HOVERED: ft.colors.BLACK
                        }
                    )
                ),
                
                ft.ElevatedButton(
                    width=900,
                    text='Adicionar ao Carrinho',
                    style=ft.ButtonStyle(
                        padding=ft.padding.all(20),
                        side={
                            ft.MaterialState.DEFAULT: ft.BorderSide(width=2, color=ft.colors.AMBER)
                        },
                        bgcolor={
                            ft.MaterialState.DEFAULT: ft.colors.AMBER
                        },
                        color={
                            ft.MaterialState.DEFAULT: ft.colors.BLACK,
                        }
                    )
                )
            ]
        )
    )
    
    layout = ft.Container(
        width=900,
        #height=200,
        margin= ft.margin.all(30),
        shadow= ft.BoxShadow(blur_radius= 30, color=ft.colors.CYAN),
        content=ft.ResponsiveRow(
            columns=12,
            spacing=0,
            run_spacing=0,
            controls=[
                product_images,
                product_datails
            ]
        )
    )
    
    page.add(layout)
    
if __name__=='__main__':
    ft.app(target=main)
