# Vim Skeleton Templates
# Learn form https://github.com/IllyaStarikov/skeleton-files/commits/master
#            http://vim.wikia.com/wiki/Use_eval_to_create_dynamic_templates


# Add the following in your ~/.vimrc file
if has("autocmd")
  augroup templates
		au!
		" Read in template files
    autocmd BufNewFile *main.* silent! execute '0r $HOME/.vim/vim-templates/skeleton-main.'.expand("<afile>:e")
    autocmd BufNewFile *.* silent! execute '0r $HOME/.vim/vim-templates/skeleton.'.expand("<afile>:e")
    " Parse special text in the templates after the read
		autocmd BufNewFile * %substitute#\[:VIM_EVAL:\]\(.\{-\}\)\[:END_EVAL:\]#\=eval(submatch(1))#ge
  augroup END
endif

