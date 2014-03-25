import os
env = Environment(ENV={'PATH': os.environ['PATH']})

enPdfOutput = env.PDF(target='geraldine_starke_en_resume.pdf', source='en-resume.tex')
Depends(enPdfOutput, Split('resume.tex'))

frPdfOutput = env.PDF(target='geraldine_starke_fr_resume.pdf', source='fr-resume.tex')
Depends(frPdfOutput, Split('resume.tex'))

dePdfOutput = env.PDF(target='geraldine_starke_de_resume.pdf', source='de-resume.tex')
Depends(dePdfOutput, Split('resume.tex'))

